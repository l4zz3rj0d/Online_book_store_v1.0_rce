# Online Book Store 1.0 – Authenticated RCE 

## Purpose

This repository documents a **working method to achieve authenticated Remote Code Execution (RCE)** in the *Online Book Store Project in PHP (v1.0)*. These notes are intended for **future reference in CTFs, labs, or revision**, not as a full write-up.

---
## Usage

modify 
```
url = "<target-url>"
```
with the valid url

add the admin username and password at 

 ```
login_data = {
    "username": "admin",
    "password": "admin",
    "login": "1"
}
```

## High-Level Working

1. Valid **admin credentials** are used to authenticate to the application.
2. An **authenticated session** is maintained using cookies.
3. The admin **book/image upload feature** is abused to upload a malicious PHP file.
4. The application fails to properly validate:

   * File extension
   * MIME type
   * Executable content
5. The uploaded file is stored in a **web-accessible directory** with PHP execution enabled.
6. The PHP payload allows execution of **OS commands via a GET parameter**, resulting in RCE.

---

## Key Indicators of Success

* Upload request returns without error
* Accessing the uploaded file via browser executes commands
* Commands run as the **web server user (e.g., www-data)**

---

## Typical Web Shell Usage

* Access the uploaded PHP file directly via its URL
* Append `?cmd=<command>` to execute system commands
* Can be upgraded to a reverse shell for stable access

---

## Vulnerability Class

* Authenticated File Upload
* Remote Code Execution (RCE)
* Improper Input Validation

---

## Notes for Future Me

* Always confirm **upload endpoint** and **upload directory** using Burp
* Paths and filenames may differ across deployments
* If command output fails, try alternate PHP execution functions
* Ideal post-exploitation step: reverse shell + privilege escalation

---

## Disclaimer

For **legal use only** in controlled environments such as CTFs, labs, or systems you own or have permission to test.
