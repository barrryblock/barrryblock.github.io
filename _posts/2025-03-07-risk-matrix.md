---
title: "Hacking the Risk Matrix: Unveiling Cybersecurity Threats"
date: 2025-03-07
---

# Hacking the Risk Matrix: Unveiling Cybersecurity Threats
*Published: March 07, 2025*  
*Author: John Prasad* 


When you hear "cybersecurity," you might picture dark rooms lit by screens, rapid typing, and perhaps some cryptic commands. Well, you're not far off! A recent project, part of my MSc in Cyber Security Engineering, brought together rigorous academic theory and real-world cybersecurity practices through a comprehensive security audit and risk assessment for a company's highly sensitive network. This assignment complemented my earlier assignment, 'Hacking the (Medical) Matrix: Risk Managing IoMT in Hospitals,' both rooted in the same module: Information Risk, Management, and Governance (IRMG). While my solo assignment focused on medical devices within healthcare, this assignment broadened the perspective, applying similar risk assessment principles to corporate cybersecurity environments in a collaborative setting.

---

## Understanding the Threat Landscape

Our mission began by identifying threats from different angles—external threats such as cybercriminals and cyberterrorists, and internal threats stemming from human factors, particularly employees susceptible to social engineering. External threat actors include cybercriminals launching attacks for financial gain (like ransomware and phishing scams), and cyberterrorists motivated by political or ideological aims, often causing widespread disruption.

Internal threats were equally crucial. Employees facing personal challenges, such as financial distress, often become inadvertent insider threats. This highlights a fundamental truth in cybersecurity: people frequently represent the weakest security link. Thus, thorough vetting and ongoing monitoring of employees’ financial and personal situations are critical elements in a robust security strategy.

---

## Inside the Red Team Operation

Our Red Team assessment rigorously tested the organization's defenses using simulated cyberattacks, structured in two phases:

- **On-site Attacks (Physical)**: Here, we assessed vulnerabilities through direct physical access to sensitive workstations.
- **Off-site Attacks (Technical)**: This involved remotely exploiting network and system vulnerabilities using advanced penetration testing techniques.

One intriguing tool we employed was the **Bad USB**, a seemingly ordinary USB device secretly loaded with malicious payloads. Our custom-configured Bad USB device executed scripts without triggering antivirus software and mapped the company's Azure Active Directory architecture via **Bloodhound**. Bloodhound proved invaluable, revealing the shortest, most vulnerable paths to escalate privileges and compromise Domain Controllers.

### Attack Scenario Spotlight

In one of our scenarios, we exploited an employee’s financial vulnerability, highlighting the reality that employees often represent the weakest link in cybersecurity:
- **Threat:** Employee under financial distress was vulnerable to bribery.
- **Exploit:** Employee inserted our compromised USB device into a critical R&D workstation.
- **Technical Impact:** Extracted sensitive R&D data, mapped the organization's entire network architecture, and executed a ransomware attack, encrypting critical files and disrupting business operations.
- **Consequences:** Severe loss of confidentiality, integrity, and availability; substantial financial losses; reputational harm; and legal repercussions due to GDPR breaches.

---

## Inside the Blue Team Operation

Our Blue Team focused on analyzing, detecting, and responding to cyber threats identified during the Red Team exercises. We employed a structured framework emphasizing compliance with key cybersecurity regulations, including GDPR. Key activities included:

- Evaluating the company's data retention policies, ensuring alignment with GDPR standards on data minimization, storage limitation, and anonymization.
- Identifying gaps in incident response procedures and recommending improvements for timely data breach reporting.
- Ensuring rigorous compliance checks and audits to maintain data integrity and operational continuity.

---

## Inside the Purple Team Operation

Combining the offensive (Red Team) and defensive (Blue Team) perspectives, our Purple Team assessments aimed to bolster the company's security posture through:

- **Collaborative Threat Simulations:** Bridging gaps between offensive and defensive teams to proactively identify and remediate vulnerabilities.
- **Security Controls Implementation:** Deployment of physical security mechanisms such as USB port locks, advanced email filtering systems, and enhanced employee training programs to address identified threats.
- **Continuous Security Validation:** Conducting regular internal phishing tests and scenario-based drills to verify the effectiveness of implemented controls.

---

## Reinforcing Cybersecurity through People, Process, and Technology

Our comprehensive assessment effectively underscored the critical importance of managing cybersecurity risks holistically. By integrating robust technical measures, structured procedural guidelines, and proactive human-factor controls, including careful employee vetting, we significantly enhanced the security posture and resilience of the organization against both external and internal threats.

---
