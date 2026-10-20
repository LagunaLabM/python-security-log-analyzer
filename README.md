# Python Security Log Analyzer and Access Control Simulation

This project is a Python notebook created as part of my studies for the **Google Cybersecurity Professional Certificate**. It simulates a basic cybersecurity workflow using sample log data to practice log parsing, IP address validation, allow-list filtering, and user/device access checks.

All data is simulated. This is an educational project, not a production security tool.

## What It Does

The notebook is organized into six steps:

### 1. Prepare Simulated Data

- Creates a sample security log (`raw_access_log.txt`) containing normal events, failed login attempts, and malformed IP-like strings.
- Creates a separate allow-list file (`master_ip_allow_list.txt`) containing the IP addresses permitted by the simulated policy.
- Defines sample users and their assigned device IDs.

### 2. Extract IP-Like Strings

- Uses Python's `re` module and a regular expression to extract strings that resemble IPv4 addresses from the log.
- This initial extraction identifies IP-like strings but does not validate whether their octets are within the valid range.

### 3. Validate IPv4 Addresses

- Defines an `is_valid_ip()` function to check that each address contains four numeric octets, each between `0` and `255`.
- Filters out malformed values, such as `256.100.100.100` and `10.0.0.999`.
- Retains repeated addresses because they may correspond to separate log events.

### 4. Compare IP Addresses Against an Allow List

- Compares the validated addresses with the simulated allow list.
- Stores valid addresses that are not on the list in `unlisted_ips`.
- Treats these results as entries requiring review, rather than automatically classifying them as malicious.

### 5. Simulate User and Device Access Checks

- Implements a reusable `check_login(username, device_id)` function.
- Checks whether a username is approved and whether the supplied device ID matches the device assigned to that user.

### 6. Test the Access-Control Function

Tests three scenarios:
- An approved user with the correct device.
- An approved user with an incorrect device.
- A user who is not on the approved list.

## What I Learned

This project gave me practical experience with core Python concepts in a cybersecurity context:

- **File handling:** Reading and writing text files using `with open()`.
- **Regular expressions:** Extracting patterns from unstructured log data with `re`.
- **Input validation:** Checking IPv4 octets using conditions, loops, and string operations.
- **List manipulation:** Filtering and comparing collections using list comprehensions and membership checks.
- **Functions:** Writing reusable functions with parameters and return values.
- **Basic access-control logic:** Checking users against assigned device IDs and testing different access outcomes.

## Acknowledgments

I wrote the core logic and Python code in this notebook. I used an AI assistant to help refine some comments and documentation.

## Limitations

This notebook uses simulated data and simplified logic. It does not perform threat-intelligence lookups, inspect live network traffic, verify passwords, or enforce access controls on a real system.

An IP address missing from the allow list is not necessarily malicious. In a production environment, additional investigation and security controls would be required. For stricter IP address validation, Python's built-in `ipaddress` module would be worth exploring.
