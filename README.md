# 🛡️ Enterprise Linux Troubleshooting & Diagnostics Portfolio

Welcome to my systems engineering ledger. This repository documents real-world production system failures, security vulnerabilities, and network infrastructure incidents diagnosed and resolved as an aspiring Cloud Support Associate. 

Every case study outlines empirical system logs, manual diagnostic pipelines, and structural remediations utilizing the industry-standard STAR framework.

---

##  Incident 01: Identity Access Management (IAM) & File Permission Remediation

* **Situation:** A critical security audit flagged a high-severity compliance violation on the corporate Web Server (`192.168.54.128`). A sensitive application configuration file containing production database credentials (`config.env`) was found misconfigured with world-writable permissions (`777`), exposing secret keys to unprivileged system users.
* **Task:** Act as the Cloud Support Associate to isolate the file's access parameters, establish a dedicated administrative group identity boundary, remediate permissions utilizing the Principle of Least Privilege (PoLP), and manually verify the secure state.
* **Action:**
  1. Audited the exposure parameters using the core file status utility:  
     `stat ~/corporate_app/config.env`
  2. Provisioned a dedicated security administrative boundary group for authorized personnel:  
     `sudo groupadd cloud_engineers`
  3. Re-assigned administrative group ownership away from unprivileged default settings:  
     `sudo chown $USER:cloud_engineers ~/corporate_app/config.env`
  4. Stripped global permissions, restricting access levels down to a hardened operational configuration:  
     `chmod 640 ~/corporate_app/config.env`
* **Result:** Successfully secured production credentials, restricted file access exclusively to verified operations staff, and validated a zero-vulnerability security baseline.

###  Proof of Work
Below is the verified terminal auditing ledger demonstrating the successfully enforced secure permissions state (`0640`).

![Identity Security Remediation](lab1_security_remediation.png)
