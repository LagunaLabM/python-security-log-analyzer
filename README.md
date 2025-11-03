# Python Security Log Analyzer & Access Control Script

This project is a Python notebook created as part of my studies for the **Google Cybersecurity Professional Certificate**. It simulates a real-world security task by ingesting a raw log file and performing a multi-phase analysis to triage threats and validate user access.

## What It Does

This script is broken down into four distinct phases, all contained within the notebook:

### Phase 1: Log Parsing (Regex Triage)
* Reads a simulated `raw_access_log.txt` file.
* Uses a Regex (Regular Expression) pattern (`re.findall()`) to parse the file and extract all IP addresses, regardless of the log entry format.

### Phase 2: Policy Filtering (IP Allow-List Check)
* Loads a `master_ip_allow_list.txt` file, which acts as the organization's "list of trusted IPs."
* Compares the extracted IPs from Phase 1 against the allow-list.
* Generates a final `suspicious_ips` list containing only the IPs that are **not** on the allow-list, flagging them for review.

### Phase 3: Authentication Logic (Access Control)
* Defines a core function `check_login(username, device_id)` to simulate a "Zero Trust" security check.
* Uses parallel lists to maintain a simple "database" of approved users and their single, assigned device.
* The function returns one of three verdicts:
    1.  **ACCESS GRANTED:** If the user and their assigned device both match.
    2.  **DEVICE MISMATCH:** If the user is valid but the device ID is not the one assigned to them.
    3.  **ACCESS DENIED:** If the user is not found in the approved list.

### Phase 4: Script Testing
* Runs a series of tests against the `check_login` function to prove the logic works for all three scenarios (Grant, Mismatch, and Deny).

## What I Learned
This project was a practical exercise in applying core Python skills to a cybersecurity problem. Key concepts I practiced include:

* **File I/O:** Reading and writing text files using `with open()`.
* **Regex:** Using the `re` module to parse and extract data from unstructured text.
* **List Manipulation:** Using loops, `if...in` statements, and `.append()` to filter data.
* **Function Definition:** Building a reusable function with clear arguments, return values, and docstrings.
* **Data Structures:** Using parallel lists to model a simple user/device database for access control.

## How to Use It
You can view the `Cybersecurity_log_analyzer.ipynb` file directly in this repository. Because it's a self-contained notebook (it creates its own log files for the simulation), you can see the code, my documentation, and the final output for each cell, all in one place.
