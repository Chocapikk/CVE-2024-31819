# AVideo CVE-2024-31819 🎥🔒💥

This Python script is an exploit for a critical unauthenticated Remote Code Execution (RCE) vulnerability found in the `WWBNIndex` plugin of the `AVideo` platform.

## ⚠️ Vulnerability Summary

The vulnerability lies in the `submitIndex.php` file of the `WWBNIndex` plugin for the `AVideo` platform. This file improperly handles user-supplied input through the `$_POST['systemRootPath']` parameter. The application uses this parameter in a `require_once` statement without sanitizing or validating the input, leading to the inclusion and execution of arbitrary PHP code.

## 📁 Affected Component

The affected component is the `submitIndex.php` file within the `WWBNIndex` plugin of the `AVideo` platform.

## 💥 Impact

This vulnerability allows unauthenticated attackers to execute arbitrary code on the server hosting the `AVideo` platform. Successful exploitation could lead to complete compromise of the server, unauthorized data access, and potential further attacks within the network infrastructure. This constitutes a severe security risk.

## 🎯 Attack Vector

The vulnerability can be exploited by sending a specially crafted POST request to the `submitIndex.php` file. This request includes a maliciously crafted `systemRootPath` parameter, exploiting the application's failure to sanitize user-supplied input properly.

## 🛠️ Mitigation

Immediate action should be taken to patch this vulnerability. The application developers should sanitize and validate all user-supplied inputs rigorously. Users of the `AVideo` platform should update the `WWBNIndex` plugin as soon as a security patch is released. Disabling the affected plugin until an update is available is also advisable to mitigate risk.

## 🔍 Affected Versions

Based on our assessments, versions 12.4 to 14.2 of the AVideo platform are vulnerable to this exploit. It is strongly recommended for administrators of the AVideo platform to review and upgrade their installations if they fall within these versions to ensure the security of their systems.

## 📜 Proof of Concept

1. An attacker generates a malicious PHP filter chain designed to execute arbitrary PHP code (e.g., using `php_filter_chain_generator.py` for `<?php system('id'); ?>`).
2. The attacker then crafts a POST request that includes this PHP filter chain in the `systemRootPath` parameter, targeting the vulnerable `submitIndex.php` endpoint.

## Usage

The script can be used as follows:

```bash
python3 AVideoExploit.py -u TARGET_URL
```

or for multiple targets:

```bash
python3 AVideoExploit.py -f URLS_FILE -t THREADS -o OUTPUT_FILE
```

Where:

- `TARGET_URL` is the base URL of the target AVideo platform.
- `URLS_FILE` is a file containing a list of target URLs.
- `THREADS` is the number of concurrent threads to use for scanning multiple targets.
- `OUTPUT_FILE` is the file to which output should be written.

## Note

This script is for educational purposes only. Do not use it for illegal activities. The author is not responsible for any misuse of this tool.
