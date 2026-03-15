# SQLScanner PRO

## Overview

SQLScanner PRO is a lightweight Python-based tool designed to detect potential SQL Injection vulnerabilities in web applications. The scanner sends predefined payloads to a target URL and analyzes the server response to identify possible vulnerabilities using error-based and time-based detection techniques.

This tool is intended for educational purposes and authorized security testing only.

## Features

* Multi-threaded scanning for faster testing
* Detection of common SQL injection patterns
* Error-based SQL injection detection
* Time-based SQL injection detection
* Generates reports in JSON and HTML format
* Simple command-line interface

## Project Structure

```
SQLScanner/
│
├── scanner.py        # Main scanning script
├── report.json       # JSON report generated after scan
├── report.html       # HTML report for easy viewing
├── report.pdf        # Optional exported report
├── results.txt       # Raw scan output
```

## Requirements

* Python 3.x
* Required Python library:

  * requests

Install dependencies using:

```
pip install requests
```

## Usage

Run the scanner using the following command:

```
python scanner.py -u <target_url>
```

Example:

```
python scanner.py -u http://example.com/page?id=1
```

## Optional Arguments

```
-u, --url        Target URL to scan (required)
-t, --threads    Number of threads for scanning (default: 10)
```

Example with custom threads:

```
python scanner.py -u http://example.com/page?id=1 -t 20
```

## How It Works

1. The tool appends SQL injection payloads to the target URL.
2. Requests are sent concurrently using multiple threads.
3. The response is analyzed for:

   * SQL error messages
   * Delayed responses indicating time-based injections.
4. If a vulnerability is detected, it is recorded in the report files.

## Output

After the scan completes, the tool generates:

* **report.json** – structured vulnerability results
* **report.html** – readable HTML report
* **results.txt** – console scan results

Example JSON entry:

```
{
    "payload": "' OR 1=1--",
    "url": "http://example.com/page?id=1' OR 1=1--",
    "type": "Error-Based"
}
```

## Disclaimer

This tool is developed strictly for educational purposes and authorized penetration testing. Do not use this tool against systems without explicit permission from the owner. The developer is not responsible for any misuse of this software.

## Author

Chiranth
