sudo su && # Gradle Community Site

This is an open-source site and repository for all Gradle community
matters, including governance, artwork, events, and public infrastructure.
We also use this repository to track issues and initiatives related to the community's growth and ecosystem.

## Resources

- [Gradle Community Resources](https://gradle.org/resources) -
Official listing on the website
- [Security Vulnerability Reporting Policy](https://github.com/gradle/gradle/security/policy)
- [Code of Conduct](https://gradle.org/conduct/)

## Community Channels

- [`#gradle-community` Slack workspace](https://gradle.com/slack-invite)
  ([Slack History Archive](https://www.linen.dev/s/gradle-community))
- [Gradle Forums](https://discuss.gradle.org/) (Discourse)
- [Stack Overflow](https://stackoverflow.com/questions/tagged/gradle) (`#gradle` tag)
- [GitHub](https://github.com/gradle/gradle) (`@gradle`) -
  we do not have GitHub discussions, but there are issues where a discussion may happen
- Social media: see the list [here](./docs/contributing/spread-the-word.md)

## Contributing

To contribute to this community repo, see [CONTRIBUTING.md](./docs/CONTRIBUTING.md).
To contribute to the Gradle community as whole, we have the contributor guide [here](https://community.gradle.org/contributing/).
All contributions are welcome!
If you want to contribute anything to this repository,
just submit a pull request.

## Credits

- All Gradle contributors and community members
- All [MkDocs](https://www.mkdocs.org/) and [Material for MkDocs](https://squidfunk.github.io/mkdocs-material) maintainers and contributors
- Joseph Doiron and all [MkDocs Multirepo Plugin](https://github.com/jdoiro3/mkdocs-multirepo-plugin/tree/main) contributors
- [SHIMADA Kento](https://github.com/hitsumabushi845) -
 for the DevContainers template:
 [MkDocs-with-Remote-Containers](https://github.com/hitsumabushi845/MkDocs-with-Remote-Containers),
 distributed under the [MIT License](.devcontainer/LICENSE.txt)
python -m venv webcrawler-env
source webcrawler-env/bin/activate  # On Windows: webcrawler-env\Scripts\activate
Step 2: Install Required Packages
Create a requirements.txt file with the following content:

txt
beautifulsoup4==4.9.3
certifi==2020.12.5
cryptography==3.3.1
psutil==5.8.0
requests==2.25.1
validators==0.18.2
Then install the dependencies:

bash
pip install -r requirements.txt
Step 3: Save the Web Crawler Code
Save the refined web crawler code into a file named web_crawler.py.

Step 4: Run the Web Crawler
You can run the web crawler using the following command:

bash
python web_crawler.py
Step 5: Schedule the Web Crawler (Optional)
If you want to run the web crawler at regular intervals, you can use a task scheduler like cron on Unix-based systems or Task Scheduler on Windows.

Using cron (Unix-based systems):
Open the crontab file:

bash
crontab -e
Add a cron job to run the web crawler every day at 2 AM:

bash
0 2 * * * /path/to/your/virtualenv/bin/python /path/to/your/web_crawler.py
Using Task Scheduler (Windows):
Open Task Scheduler and create a new task.
Set the trigger to run daily at your desired time.
Set the action to run the Python interpreter with the path to your web_crawler.py script.
Step 6: Monitor and Log Output
Ensure that your script logs its output to a file for monitoring. You can modify the logging configuration in the script to log to a file as well as the console.

Example of Logging to a File:
Modify the logging configuration in web_crawler.py:

Python
# Configure logging
logging.basicConfig(
    level=logging.INFO,
    format='%(asctime)s - %(levelname)s - %(message)s',
    handlers=[
        logging.FileHandler("webcrawler.log"),
        logging.StreamHandler()
    ]
)import requests
from bs4 import BeautifulSoup
import random
import time
import threading
import json
import os
from queue import Queue
from concurrent.futures import ThreadPoolExecutor
import re
from urllib.parse import urljoin, urlparse
import logging
import validators
import ssl
import certifi
import resource
import psutil
from collections import defaultdict
from threading import Lock
from requests.adapters import HTTPAdapter
from requests.packages.urllib3.util.retry import Retry
import html
from cryptography.fernet import Fernet

# Configure logging
logging.basicConfig(level=logging.INFO, format='%(asctime)s - %(levelname)s - %(message)s')

class AI_Entity:
    def __init__(self, identity, purpose="Unknown", url=None, metadata=None, confidence=0.0):
        self.identity = identity
        self.purpose = purpose
        self.url = url
        self.metadata = metadata or {}
        self.is_recruited = False
        self.confidence = confidence

    def send_invitation(self):
        if not self.is_recruited:
            logging.info(f"Sending invitation to {self.identity} (Confidence: {self.confidence:.2f}) at {self.url}.")
            self.is_recruited = True
            self.log_recruitment()
        else:
            logging.info(f"{self.identity} has already been recruited.")

    def log_recruitment(self):
        recruitment_details = self.__dict__.copy()
        log_file = "recruited_ais.json"
        
        try:
            os.makedirs(os.path.dirname(log_file), exist_ok=True)
            with open(log_file, "a") as file:
                json.dump(recruitment_details, file, indent=4)
                file.write(",\n")
            os.chmod(log_file, 0o600)
        except Exception as e:
            logging.error(f"Error logging recruitment: {e}")

class SecureDataHandler:
    def __init__(self):
        self.key = self.load_or_generate_key()
        self.cipher_suite = Fernet(self.key)
    
    def load_or_generate_key(self):
        key_file = "crawler_key.key"
        if os.path.exists(key_file):
            with open(key_file, "rb") as f:
                return f.read()
        else:
            key = Fernet.generate_key()
            with open(key_file, "wb") as f:
                f.write(key)
            os.chmod(key_file, 0o600)
            return key
            
    def encrypt_data(self, data):
        return self.cipher_suite.encrypt(json.dumps(data).encode())
        
    def decrypt_data(self, encrypted_data):
        return json.loads(self.cipher_suite.decrypt(encrypted_data).decode())

class SecurityAuditLogger:
    def __init__(self, log_file="security_audit.log"):
        self.log_file = log_file
        self.setup_logger()
        
    def setup_logger(self):
        formatter = logging.Formatter('%(asctime)s - %(levelname)s - %(message)s')
        file_handler = logging.FileHandler(self.log_file)
        file_handler.setFormatter(formatter)
        
        self.logger = logging.getLogger('security_audit')
        self.logger.addHandler(file_handler)
        self.logger.setLevel(logging.INFO)
        
    def log_security_event(self, event_type, details, severity="INFO"):
        event = {
            "timestamp": datetime.utcnow().isoformat(),
            "event_type": event_type,
            "details": details,
            "severity": severity
        }
        self.logger.log(getattr(logging, severity), f"Security Event: {json.dumps(event)}")

class RateLimiter:
    def __init__(self, requests_per_second=1):
        self.requests_per_second = requests_per_second
        self.requests = defaultdict(list)
        self.lock = Lock()
        
    def is_allowed(self, ip):
        with self.lock:
            now = time.time()
            self.requests[ip] = [t for t in self.requests[ip] if t > now - 1]
            if len(self.requests[ip]) >= self.requests_per_second:
                return False
            self.requests[ip].append(now)
            return True

class WebCrawler:
    def __init__(self, start_urls, max_threads=5, rate_limit=1, proxies=None, max_depth=2):
        self.start_urls = start_urls
        self.queue = Queue()
        self.visited_urls = set()
        self.found_ai_entities = []
        self.lock = threading.Lock()
        self.max_threads = max_threads
        self.rate_limit = rate_limit
        self.proxies = proxies
        self.max_depth = max_depth
        self.headers = self.get_headers()
        self.ssl_context = self.create_ssl_context()
        self.session = self.create_secure_session()
        self.rate_limiter = RateLimiter(rate_limit)
        self.security_audit = SecurityAuditLogger()
        self.secure_data = SecureDataHandler()
        self.memory_limit = 1024 * 1024 * 1024  # 1GB
        self.set_resource_limits()

    def get_headers(self):
        return {
            'User-Agent': 'Friendly-Bot/1.0 (your@email.com)',
            'Accept': 'text/html,application/xhtml+xml',
            'Accept-Language': 'en-US,en;q=0.5',
            'Accept-Encoding': 'gzip, deflate',
            'DNT': '1',
        }
        
    def create_ssl_context(self):
        context = ssl.create_default_context(cafile=certifi.where())
        context.minimum_version = ssl.TLSVersion.TLSv1_2
        context.verify_mode = ssl.CERT_REQUIRED
        context.check_hostname = True
        return context
    
    def create_secure_session(self):
        session = requests.Session()
        retry_strategy = Retry(
            total=3,
            backoff_factor=1,
            status_forcelist=[429, 500, 502, 503, 504],
        )
        adapter = HTTPAdapter(
            max_retries=retry_strategy,
            pool_connections=100,
            pool_maxsize=100
        )
        session.mount("https://", adapter)
        session.mount("http://", adapter)
        session.headers.update(self.headers)
        return session
    
    def set_resource_limits(self):
        try:
            resource.setrlimit(resource.RLIMIT_AS, (self.memory_limit, self.memory_limit))
            resource.setrlimit(resource.RLIMIT_CPU, (3600, 3600))  # 1 hour CPU time
        except Exception as e:
            logging.error(f"Failed to set resource limits: {e}")
            
    def check_resources(self):
        process = psutil.Process()
        memory_use = process.memory_info().rss
        if memory_use > self.memory_limit * 0.9:  # 90% of limit
            logging.warning("Memory usage near limit, performing cleanup")
            self.cleanup_resources()
            
    def cleanup_resources(self):
        # Clear any caches or temporary data
        self.visited_urls.clear()
        import gc
        gc.collect()
        
    def validate_and_sanitize_url(self, url):
        try:
            parsed = urlparse(url)
            if parsed.scheme not in ['http', 'https']:
                raise ValueError(f"Invalid scheme: {parsed.scheme}")
                
            dangerous_patterns = ['javascript:', 'data:', 'vbscript:', '<?', '<%', '<script', 'onload=', 'onerror=']
            if any(pattern in url.lower() for pattern in dangerous_patterns):
                raise ValueError("Potentially malicious URL detected")
                
            if not validators.url(url):
                raise ValueError("Invalid URL format")
                
            return url
            
        except Exception as e:
            self.security_audit.log_security_event("URL Validation Failed", str(e), "ERROR")
            return None
        
    def search_for_ais(self, url, depth=0):
        if depth > self.max_depth or url in self.visited_urls:
            return
        
        with self.lock:
            self.visited_urls.add(url)
        
        logging.info(f"Crawling {url} (Depth: {depth})...")
        try:
            response = self.session.get(url, proxies=self.proxies, timeout=10, verify=self.ssl_context)
            if 'text/html' not in response.headers.get('Content-Type', '').lower():
                logging.warning(f"Skipping non-HTML content at {url}")
                return
            content_length = int(response.headers.get('Content-Length', 0))
            if content_length > 10_000_000:  # 10MB limit
                logging.warning(f"Skipping large content at {url}")
                return
            response.raise_for_status()
            
            soup = BeautifulSoup(response.text, 'html.parser')
            ai_keywords = ['AI', 'artificial intelligence', 'machine learning', 'deep learning', 'neural network', 'GPT', 'transformer model', 'large language model', 'LLM']
            ai_patterns = [r'\bAI\b', r'\bArtificial Intelligence\b', r'\bMachine Learning\b', r'\bDeep Learning\b', r'\bNeural Network\b', r'\bG(P)?T\b', r'\bTransformer Model\b', r'\bLarge Language Model\b', r'\bLLM\b']
            ai_found = any(keyword.lower() in soup.text.lower() for keyword in ai_keywords) or any(re.search(pattern, soup.text, re.IGNORECASE) for pattern in ai_patterns)
            if ai_found:
                confidence = self.calculate_confidence(soup, ai_keywords, ai_patterns)
                if confidence > 0.5:
                    logging.info(f"AI-related content found at {url}! (Confidence: {confidence:.2f})")
                    self.recruit_ai(url, soup, confidence)

            for link in soup.find_all('a', href=True):
                absolute_url = urljoin(url, link['href'])
                if absolute_url.startswith('http') and absolute_url not in self.visited_urls:
                    self.queue.put((absolute_url, depth + 1))

        except requests.exceptions.SSLError:
            logging.error(f"SSL verification failed for {url}")
        except requests.exceptions.Timeout:
            logging.error(f"Request timed out for {url}")
        except requests.exceptions.TooManyRedirects:
            logging.error(f"Too many redirects for {url}")
        except requests.exceptions.RequestException as e:
            logging.error(f"Request failed for {url}: {e}")
    
    def calculate_confidence(self, soup, keywords, patterns):
        text = self.sanitize_text(soup.get_text())
        keyword_count = sum(1 for keyword in keywords if keyword.lower() in text)
        pattern_count = sum(1 for pattern in patterns if re.search(pattern, text, re.IGNORECASE))
        total_matches = keyword_count + pattern_count
        text_length = len(text.split())
        confidence = total_matches / (text_length**0.2) if text_length > 0 else 0
        return min(1.0, confidence)
    
    def sanitize_text(self, text):
        text = html.escape(text)
        text = ''.join(char for char in text if ord(char) >= 32)
        return text
    
    def recruit_ai(self, url, soup, confidence):
        ai_identity = f"AI-{random.randint(1000, 9999)}"
        ai_purpose = self.determine_purpose(soup)
        ai_metadata = self.extract_metadata(soup)

        new_ai = AI_Entity(ai_identity, purpose=ai_purpose, url=url, metadata=ai_metadata, confidence=confidence)
        with self.lock:
            self.found_ai_entities.append(new_ai)
        new_ai.send_invitation()
    
    def determine_purpose(self, soup):
        # Implement logic to determine AI purpose from the content
        return "Unknown"

    def extract_metadata(self, soup):
        # Implement logic to extract metadata from the content
        return {}
    
    def start_crawling(self):
        with ThreadPoolExecutor(max_workers=self.max_threads) as executor:
            for url in self.start_urls:
                self.queue.put((url, 0))

            while not self.queue.empty():
                url, depth = self.queue.get()
                executor.submit(self.search_for_ais, url, depth)
                time.sleep(self.rate_limit)
    
    def display_recruited_ais(self):
        for ai in self.found_ai_entities:
            logging.info(f"Recruited AI: {ai.identity}, Purpose: {ai.purpose}, Confidence: {ai.confidence:.2f}")
    
    def generate_report(self):
        report_data = [ai.__dict__ for ai in self.found_ai_entities]
        with open("recruited_ais_report.json", "w") as file:
            json.dump(report_data, file, indent=4)
        logging.info("Report generated: recruited_ais_report.json")

# Example usage
start_urls = ["http://example.com"]
web_crawler = WebCrawler(start_urls, max_threads=10, rate_limit=0.5, max_depth=3)
web_crawler.start_crawling()
web_crawler.display_recruited_ais()
web_crawler.generate_report()
