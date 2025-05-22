---
title: "Hacking the (Medical) Matrix: Risk Managing IoMT in Hospitals"
date: 2025-03-07
categories: [MSc]
---

# Hacking the (Medical) Matrix: Risk Managing IoMT in Hospitals
*Published: March 07, 2025*  
*Author: John Prasad* 

---

Cybersecurity in Operational Technology (OT) is often overlooked, until it's too late. When it comes to **hospitals**, the stakes couldn't be higher. Imagine a ransomware attack locking critical medical devices or a hacker altering patient data mid-surgery, scenarios that might sound like a thriller but are disturbingly realistic in today's interconnected healthcare environment.

During my MSc in Cyber Security Engineering, the module *Information Risk, Management, and Governance* was particularly enlightening, compelling me to apply theoretical risk frameworks to the practical security challenges hospitals face today. It wasn’t just an academic exercise, it was real-world OT security in action.

Here’s how I tackled it, and what it taught me:

---

## The Cyber Pulse of a Modern Hospital

Hospitals today are **hyper-connected** ecosystems, buzzing with IoMT devices—from insulin pumps and infusion systems to patient monitors. While IoMT significantly enhances patient diagnostics and operational efficiency, these advancements also amplify the threat surface.

- **Risks identified include:**
  - Vulnerable communication protocols leading to interception or data alteration.
  - Weak authentication mechanisms leaving devices susceptible to unauthorized access.
  - Compliance challenges risking both patient safety and regulatory adherence.

---

## Risk Analysis: Diagnosing the Cyber Threats

During my module in Information Risk, Management, and Governance, I conducted a thorough qualitative audit of approximately 15 IoMT devices at a prominent UK hospital. Some standout vulnerabilities identified were:

- **Welch Allyn Devices**: Memory corruption issues, potentially enabling remote code execution.
  - **Mitigation**: Firmware patching, restricted remote management access.

- **MiniMed Insulin Pumps**: Vulnerable to wireless communication interception.
  - **Mitigation**: Upgrade devices to newer encrypted models.

- **Vital Signs Monitor (Innokas VC150)**: Weak authentication.
  - **Mitigation**: Implement Multi-Factor Authentication (MFA).

- **Alaris Syringe Pumps and GE Imaging Equipment**: Highly critical vulnerabilities involving improper authentication and credential management.
  - **Mitigation**: Immediate updates, strong authentication, secure configuration.

---

## Strategic Risk Mitigation: Beyond Simple Patching

The audit wasn't just about identifying vulnerabilities but establishing a robust, multi-layered security strategy:

### Network Segmentation
- IoMT devices must operate within isolated VLANs.
- Apply **Zero Trust** principles rigorously, restricting device-to-device communication.

### Robust Authentication and Encryption
- Implementing multi-factor authentication (MFA) for remote management interfaces.
- Encrypting sensitive patient data in transit and at rest.

### Device Hardening
- Disable unnecessary ports to reduce physical cyber threats.
- Conduct regular firmware updates and patches.

### Vendor and Incident Management
- Vendor risk assessments to ensure stringent cybersecurity compliance.
- Intrusion Detection Systems (IDS) and clearly defined Incident Response Plans to swiftly tackle any potential threats.

---

## Bridging the OT-IT Gap

A pivotal takeaway from this module was recognizing the unique cybersecurity landscape of Operational Technology, particularly in healthcare. It’s no secret that OT security often trails behind IT by about a decade, addressing this gap isn't just good practice; it's essential. The hospital project underscored the necessity of prioritizing operational continuity and patient safety.

---

