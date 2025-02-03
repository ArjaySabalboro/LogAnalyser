# Log Analysis Script

This is a shell script that analyzes web server log files and provides insights such as:
- Top 5 IP addresses with the most requests
- Top 5 most requested paths
- Top 5 response status codes
- Top 5 user agents

## Requirements
- Linux/macOS with a shell environment
- `awk`, `sort`, `uniq` (pre-installed on most Unix-based systems)

## Installation
1. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/log-analysis.git
   cd log-analysis
   ```
2. Make the script executable:
   ```bash
   chmod +x analyze_logs.sh
   ```

## Usage
Run the script with a log file as an argument:
```bash
./analyze_logs.sh access.log
```

## Example Log Entry
```
178.128.94.113 - - [04/Oct/2024:00:00:18 +0000] "GET /v1-health HTTP/1.1" 200 51 "-" "DigitalOcean Uptime Probe 0.22.0 (https://digitalocean.com)"
```

## Sample Output
```
Analyzing log file: access.log

Top 5 IP addresses with the most requests:
178.128.94.113 - 50 requests
45.76.135.253 - 40 requests
192.168.0.1 - 20 requests
10.0.0.2 - 10 requests
142.93.143.8 - 5 requests

Top 5 most requested paths:
/v1-health - 70 requests
/api/v1/products - 50 requests
/api/v1/orders - 20 requests
/api/v1/users - 10 requests
/api/v1/payments - 5 requests

Top 5 response status codes:
200 - 120 requests
404 - 30 requests
500 - 10 requests
301 - 5 requests
401 - 2 requests

Top 5 user agents:
DigitalOcean Uptime Probe 0.22.0 (https://digitalocean.com) - 80 requests
Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 - 30 requests
curl/7.68.0 - 20 requests
Python-urllib/3.8 - 10 requests
PostmanRuntime/7.29.0 - 5 requests
```

## License
This project is licensed under the MIT License.

## Author
[Arjay Sabalboro] - [Github](https://github.com/ArjaySabalboro/)

