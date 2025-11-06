# Python Security Log Analyzer & Access Control Script

This project is a Python notebook created as part of my studies for the **Google Cybersecurity Professional Certificate**. It simulates a real-world security task by ingesting a raw log file and performing a multi-phase analysis to triage threats and validate user access.

## What It Does

This script is broken down into multiple phases, all contained within the notebook:

### Phase 1: Log Parsing (Regex Triage)
* Reads a simulated `raw_access_log.txt` (which includes well-formed and malformed IPs).
* Uses a broad Regex (Regular Expression) pattern to parse the file and extract all strings that *look* like an IP address.

### Phase 1.5: IP Validation
* **(This phase was added after receiving expert community feedback)**
* Defines and runs a `is_valid_ip` function to filter the raw list from Phase 1.
* This function checks that each IP has four octets and that each octet is a valid digit between `0` and `255`.
* It successfully filters out malformed IPs (e.g., `256.100.100.100` or `10.0.0.999`), and the results are printed in the notebook output.

### Phase 2: Policy Filtering (IP Allow-List Check)
* Takes the new, *clean* `valid_ips` list.
* Compares the valid IPs against the `master_ip_allow_list.txt`.
* Generates a final `suspicious_ips` list containing only the IPs that are valid but not on the allow-list.

### Phase 3 & 4: Authentication Logic & Testing
* Defines and tests a separate, modular function `check_login(username, device_id)` to simulate a "Zero Trust" security policy (checking both user and device).

## What I Learned
This project was a practical exercise in applying core Python skills to a cybersecurity problem. Key concepts I practiced include:

* **File I/O:** Reading and writing text files using `with open()`.
* **Regex:** Using the `re` module to parse unstructured text.
* **List Manipulation:** Using loops, `if...in` statements, and list comprehensions to filter data.
* **Function Definition:** Building reusable, documented functions (`is_valid_ip`, `check_login`) to create modular and testable code.

## Acknowledgments & Project Iteration

The core logic and all Python code in this notebook were written by me. I used an AI assistant to help refine the in-code comments and documentation.

**Special Thanks:** After sharing this project, I received expert feedback from a member of the Google Cybersecurity community who pointed out that my initial Regex did not *validate* IP addresses.

Based on that feedback, I researched and implemented **Phase 1.5: IP Validation**. This demonstrates the critical importance of community feedback, robust input validation, and iterative development.
