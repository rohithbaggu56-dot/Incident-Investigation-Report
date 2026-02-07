# 🚨 Incident Investigation Report – SSH Brute Force Attack (Lab Simulation)


## 📌 Overview

This report documents a simulated security investigation performed in a home SOC lab environment.  
The goal was to understand how a brute-force SSH attack appears in logs and how a SOC analyst investigates, validates, and documents suspicious activity.

⚠️ **Note:** This investigation was conducted using **simulated log data** for learning purposes.



## 🎯 Objective

- Practice SOC-style incident investigation
- Identify brute-force behavior in SSH logs
- Correlate events to determine attacker activity
- Extract Indicators of Compromise (IOCs)
- Document findings in a clear and structured manner



## 🧰 Tools Used

- **Splunk SIEM** – log search, analysis, and dashboards  
- **Linux SSH Logs** – authentication activity  
- **SPL (Search Processing Language)** – querying and filtering events  



## 🧠 Background 

SSH (Secure Shell) is used to remotely access Linux systems.  
Attackers often try to guess usernames and passwords by repeatedly attempting logins, this is known as a **brute-force attack**.

In real SOC environments, these attacks are very common and must be detected early.



## 🔍 Investigation Process


### 1️⃣ Initial Alert Observation

The investigation started after noticing:
- A **high number of failed SSH login attempts**
- Repeated attempts from the **same IP addresses**
- Login attempts using **common or invalid usernames** (e.g., `root`, `admin`, `test`)

This behavior is **not normal** for legitimate users.




### 2️⃣ Log Analysis (What I Checked)

Using Splunk, I analyzed SSH authentication logs and focused on:
- Failed login events
- Source IP addresses
- Targeted usernames
- Frequency and timing of attempts

Patterns showed:
- Multiple failures within short time intervals
- Same IP trying different usernames
- Attempts continuing until the connection was blocked or dropped



### 3️⃣ Suspicious Indicators Identified

The following behaviors confirmed malicious intent:

- 🔁 **Repeated failed authentication attempts**
- 🌍 **Geographically unusual IP addresses**
- 👤 **Multiple username guessing from one IP**
- ⏱️ **Rapid login attempts (automation behavior)**

These are classic indicators of an SSH brute-force attack.



## 🧾 Indicators of Compromise (IOCs)

| Type        | Indicator Example |
|------------|------------------|
| IP Address | Suspicious external IPs attempting logins |
| Username  | `root`, `admin`, `test`, `backup` |
| Activity  | Multiple failed SSH authentication attempts |



## 📊 Dashboards & Visualization
To better understand the activity, dashboards were created showing:
- Total SSH login attempts
- Successful vs failed logins
- Top attacking IP addresses
- Most targeted usernames
- Geographic distribution of attacks

![Splunk SSH-log-dashboard](https://github.com/user-attachments/assets/07db8c52-3043-404a-9e0d-665d003144ba)




## 🛡️ Analyst Conclusion

Based on log patterns and behavior:
- This activity is classified as a **Brute-Force SSH Attack**
- The intent was to gain unauthorized access
- No successful compromise was confirmed in this simulation



## 🧠 What a SOC Analyst Would Do Next

In a real environment, the next steps would include:
- Blocking attacker IPs via firewall
- Enforcing SSH key-based authentication
- Disabling root login over SSH
- Creating alerts for repeated failed logins
- Notifying system administrators



## ✅ Skills Demonstrated

- SOC investigation workflow
- Log analysis and correlation
- Identifying malicious behavior
- IOC extraction
- Clear security documentation
- Defensive thinking mindset

---
🔗 **Navigation**  
⬅️ [Back to Portfolio](https://github.com/rohithbaggu56-dot)
---

