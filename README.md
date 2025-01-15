Cybersecurity Projects

# Linux Privilege Escalation

## Project Overview
This project involved performing **privilege escalation** on a vulnerable Linux machine hosted on Hack The Box (Machine: "Beep") or TryHackMe (Room: "Linux Privilege Escalation"). The objective was to gain root access by exploiting misconfigurations in the Linux environment.

### Tools Used:
- **LinPEAS** - A tool for automating the enumeration of privilege escalation vectors.
- **Linux Exploit Suggester** - Helps identify potential exploits based on system details.
- **GTFObins** - A collection of Unix binaries that can be exploited for privilege escalation.
- **Sudo** - Misconfigured sudoers file used for privilege escalation.

### Steps Taken:
1. **Initial Access:**
   - Gained initial access via a simple SSH login using weak credentials.

2. **Privilege Escalation Enumeration:**
   - Ran **LinPEAS** and **Linux Exploit Suggester** to enumerate possible privilege escalation vectors, including weak file permissions and exploitable binaries.
   
3. **Exploit Discovery:**
   - Identified a misconfigured **sudoers** file, where a user had permission to run a vulnerable script as root without a password.
   - Used **GTFObins** to identify a potential **SUID** binary vulnerability.

4. **Exploitation:**
   - Exploited the **sudoers file misconfiguration** to execute arbitrary commands as root.
   - Escalated to root by exploiting **SUID binaries**.

### Outcome:
Successfully escalated privileges from a regular user to root. Documented the exploited vulnerabilities and provided recommendations to prevent similar escalations.

### Screenshots:
- [Initial Shell Access](./Screenshots/initial_shell.png)
- [Privilege Escalation via Sudo](./Screenshots/sudo_exploit.png)

---

## Lessons Learned:
- Gained hands-on experience in Linux privilege escalation techniques.
- Learned to enumerate potential vulnerabilities using tools like LinPEAS and Linux Exploit Suggester.
- Developed a deeper understanding of **Sudo** misconfigurations and **SUID binaries**.

---

## Remediation Recommendations:
1. **Sudo Configuration:**
   - Restrict users from running commands as root unless absolutely necessary.
   - Use the `NOPASSWD` directive carefully, avoiding unnecessary command execution.
   
2. **SUID Binaries:**
   - Regularly audit SUID binaries and ensure they are needed for system functionality.
   - Correct improper file permissions.

---








# Privilege Escalation Report

## Target System: Beep (HTB) / Linux Privilege Escalation (TryHackMe)

### Exploits Found:
1. **Sudo Misconfiguration**
   - **Description:** The user had sudo permissions to run a vulnerable script without needing to enter a password.
   - **Exploitation:** Gained root access by executing arbitrary commands as root using **sudo**.
   - **Severity:** High
   - **Remediation:** Restrict the use of sudo and avoid unnecessary root-level privileges.

2. **SUID Binary Exploitation**
   - **Description:** A SUID binary was discovered that could be exploited to escalate privileges.
   - **Exploitation:** Used the SUID binary to execute commands with root privileges.
   - **Severity:** Medium
   - **Remediation:** Regularly audit SUID binaries and correct any misconfigurations.

### Conclusion:
Privilege escalation was successfully achieved using misconfigurations in sudoers and SUID binaries. Immediate remediation is recommended to mitigate the risks of privilege escalation.



