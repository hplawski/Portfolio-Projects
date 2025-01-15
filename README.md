Cybersecurity Projects

# Web Application Vulnerability Assessment

## Project Overview
This project involved conducting a **vulnerability assessment** and **penetration testing** on a vulnerable web application hosted on Hack The Box (Machine: "Juice Shop") or TryHackMe (Room: "OWASP Top 10"). The main objective was to identify and exploit common web application vulnerabilities, including **SQL Injection**, **Cross-Site Scripting (XSS)**, and **Insecure Direct Object Reference (IDOR)**.

### Tools Used:
- **Burp Suite** - Used for intercepting and modifying HTTP requests, scanning for vulnerabilities.
- **SQLmap** - Automated SQL Injection exploitation tool.
- **Nikto** - Web server scanner to find potential misconfigurations and vulnerabilities.
- **Gobuster** - Directory and file brute force tool to discover hidden resources.

### Steps Taken:
1. **Reconnaissance:**
   - Used **Nmap** for network scanning and identifying open ports on the target machine.
   - Performed web application enumeration with **Gobuster** to discover hidden directories.
   - Ran **Nikto** for initial vulnerability scanning.

2. **Vulnerability Discovery:**
   - **SQL Injection:**
     - Exploited an SQL injection vulnerability on the login form using **SQLmap** to dump the database.
   - **Cross-Site Scripting (XSS):**
     - Identified and exploited reflected XSS vulnerability to steal session cookies.
   - **IDOR (Insecure Direct Object Reference):**
     - Exploited a URL parameter flaw to access restricted user accounts.

3. **Exploitation:**
   - **SQL Injection:** Dumped sensitive data such as usernames, passwords, and other confidential information.
   - **XSS:** Used a crafted XSS payload to steal cookies, simulating a session hijacking attack.
   - **IDOR:** Gained unauthorized access to restricted resources.

4. **Post-Exploitation:**
   - Analyzed the impact of the vulnerabilities and provided recommendations for remediation.

### Outcome:
Successfully identified several critical vulnerabilities, including SQL Injection, XSS, and IDOR. Remediations suggested include input validation, proper sanitization, and secure coding practices.

### Report:
A detailed vulnerability report is available in the **Reports** folder.

### Screenshots:
- [SQL Injection Exploitation](./Screenshots/sql_injection.png)
- [XSS Exploit in Action](./Screenshots/xss_attack.png)

---

## Lessons Learned:
- Gained hands-on experience in exploiting common web vulnerabilities.
- Learned to use common penetration testing tools like Burp Suite and SQLmap.
- Developed an understanding of web application security principles, including OWASP Top 10.

---

## Remediation Recommendations:
1. **SQL Injection:**
   - Use prepared statements and parameterized queries.
   - Apply input sanitization to user inputs.

2. **Cross-Site Scripting (XSS):**
   - Implement proper input sanitization and output encoding.
   - Use Content Security Policy (CSP) headers.

3. **Insecure Direct Object Reference (IDOR):**
   - Use strong access control checks and validate user input.

---















# Vulnerability Assessment Report

## Target Application: Juice Shop (HTB) / OWASP Top 10 (TryHackMe)

### Vulnerabilities Found:
1. **SQL Injection**
   - **Location:** Login page (POST request)
   - **Description:** The application was vulnerable to SQL Injection, allowing an attacker to inject SQL queries into the database through the login form.
   - **Exploitation:** Used **SQLmap** to extract the usernames and passwords from the database.
   - **Severity:** High
   - **Remediation:** Use prepared statements and parameterized queries.

2. **Cross-Site Scripting (XSS)**
   - **Location:** Search field
   - **Description:** The search feature did not sanitize user input, allowing an attacker to inject malicious JavaScript code.
   - **Exploitation:** Injected a script to steal session cookies.
   - **Severity:** Medium
   - **Remediation:** Implement input sanitization and output encoding to prevent XSS.

3. **Insecure Direct Object Reference (IDOR)**
   - **Location:** URL parameter for accessing user accounts
   - **Description:** The application allowed unauthorized users to modify the URL and access other user’s resources.
   - **Exploitation:** Accessed restricted user information by manipulating the URL.
   - **Severity:** Medium
   - **Remediation:** Validate user input and implement proper access control mechanisms.

### Conclusion:
The application was found to be vulnerable to common security issues such as SQL Injection, XSS, and IDOR. Immediate remediation is recommended to prevent exploitation.




