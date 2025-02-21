# Cyber Security Trends Shaping Our Digital Public Infrastructure

*Published: February 21, 2025*  
*Author: John Prasad*  

> “In the age of digital everything, protecting identities isn’t just a best practice—it’s a matter of survival.”

---

## Introduction

Welcome to my very first blog post on cybersecurity! While that might sound like the beginning of a snooze-fest, I promise you this ride will be filled with witty anecdotes, glaring red flags, and plenty of “really, they hacked _that_?” moments. Strap in, because it’s time to talk about how our digital infrastructures—those vital services we rely on every day—are under siege by sneaky ransomware gangs, shadowy state-sponsored attackers, and some downright audacious amateurs who’ve watched way too many hacker movies.

But don’t just take my word for it. I recently prepared a report for the Alan Turing Institute on **Cyber Trends in Digital Public Infrastructure** (yes, that Alan Turing—father of modern computing, codebreaker extraordinaire, and all-around genius). Let’s unpack some of the key points from this research and, most importantly, discover what on earth we can do to protect ourselves. 

---

## Cyber Threats: The Highlights Reel

### 1. Ransomware: Pay Up or Pack Up
Ransomware is the seasoned pickpocket of the cyber world—slipping into your systems, encrypting data, and demanding a hefty ransom for its release. From healthcare facilities losing access to patient records to local governments freezing out their residents’ data, it’s high-stakes extortion that can put daily life on hold.  

In 2024, we saw healthcare systems, municipalities, and even financial institutions grind to a halt under these threats. For instance, NHS pathology testing provider Synnovis was hit, exposing sensitive patient data and disrupting thousands of appointments [^1]. LoanDepot, a major US mortgage lender, also saw 16.6 million customer records compromised [^2]. City governments, such as Columbus, Ohio, faced significant upheaval, with personal data of over half its residents at risk [^3]. 

**Pro Tip:** Regularly back up your data and test your recovery process. Otherwise, you could be stuck paying the digital equivalent of protection money.

### 2. Zero-Day Exploits: Guess Who Didn’t Update?
A zero-day exploit is like a skeleton key hackers discover before anyone else even knows it exists. This means vendors haven’t patched it, and you’re left hoping your firewall has had its morning coffee. Ivanti Connect Secure is one example that saw widespread exploitation [^4].   

**Pro Tip:** Patch early, patch often. And if your system admin says, “We’ll patch it tomorrow,” buy them coffee and gently suggest doing it _today_.

### 3. Supply Chain Attacks: Targeting the Middle Man
Instead of going after a big corporation’s heavily fortified servers, threat actors often infiltrate a third-party supplier who holds the keys to the castle. One breach can mean a domino effect of catastrophic proportions, hitting multiple companies—and sometimes entire government agencies. 

Supply chain attacks soared in 2024, with the Snowflake compromise standing out. Threat actors stole credentials from multiple organizations, including Ticketmaster, Santander Bank, and AT&T, all because they compromised a multi-cloud data warehousing platform [^5]. In another incident, vulnerabilities in the MOVEit file transfer system led to breaches at Amazon and Delta Airlines [^6].  

**Pro Tip:** Ensure your vendors follow strict security standards. If your chain is only as strong as its weakest link, you’d better confirm none of them are made of sugar.

### 4. State-Sponsored Espionage: The Shadow Game
From infiltration of government agencies to email breaches affecting entire departments, cyber espionage campaigns are no longer just in Hollywood spy thrillers. 

The Storm-0558 hacking group exploited Microsoft’s authentication tokens, infiltrating US government email accounts [^7]. Volt Typhoon, another group allegedly backed by Chinese state sponsorship, infiltrated critical infrastructure sectors, from communications to water supply [^8].  

**Pro Tip:** Zero Trust Architecture. Verify everyone and everything. Yes, even your printer.

### 5. Data Brokers & Identity: The Unseen Risk
You know all those background check services offering any detail on someone for the cost of a latte? Sometimes they get hacked, and _your_ info is part of the loot. Then we have national identity breaches where entire populations’ biometric data, addresses, and phone numbers are posted in the dark corners of the internet[^11]. 

A breach at National Public Data exposed sensitive information (possibly including Social Security numbers) of millions of people across multiple countries [^9]. Meanwhile, a massive breach in El Salvador’s national digital infrastructure compromised the personal data of 5.1 million citizens—including biometric facial photos [^10]—highlighting how national identity systems can become gold mines for cybercriminals.


**Pro Tip:** Implement robust encryption and multi-factor authentication. Demand that organizations handling your data do the same—or at least send them a strongly worded email.

---

## Future Trends (And Why We Should Worry Now)

1. **Generative AI and Social Engineering**  
   Attackers are using AI-generated text, voices, and even videos to scam unsuspecting users. It’s getting harder to tell fact from fiction.  

2. **Global Regulatory Wake-Up Calls**  
   Expect more governments to wake up and draft heavy-handed legislation. Some might help, but watch out for any half-baked rules that create as many problems as they solve.

3. **Machine Identities**  
   With automation rising, machine-to-machine communication is exploding—but so are the security risks. Many organizations have no idea how many “machine IDs” they even have.  
  
4. **Resurgence of Old-School Techniques**  
   While new tech is flashy, sometimes simple phishing, password spraying, or phone-based scams remain the easiest way in. As we harden the perimeter, criminals might slip in through the back door labelled “human error.”

---

## Actionable Insights: From Panic to Plan

So, how do we protect ourselves from this relentless barrage of threats? Here’s a quick cheat sheet:

1. **Adopt a Zero Trust Mindset**  
   Trust no one and nothing by default. Verify all user, device, and application interactions.  
   > Example: Configure strict network segments so that if an attacker compromises a single workstation, they don’t waltz into your entire environment.

2. **Embrace Regular Risk Assessments**  
   Map out your vulnerabilities using frameworks like **NIST Cybersecurity Framework (CSF)**, **CIS Controls**, **FAIR (Factor Analysis of Information Risk)**, **ISO 27001**, and the **Cyber Kill Chain**. Keep an up-to-date risk register and measure the impact vs. likelihood of each threat.  
   > Example: A high-likelihood threat that can cause severe disruption (like a supply chain attack) should shoot straight to the top of your priority list.

3. **Backups: Versioning Is Your Friend**  
   A backup that’s six months old might not cut it. Keep multiple versions in multiple secure locations. If ransomware hits, you’ll thank yourself.

4. **Train, Train, and Train Some More**  
   Humans are still the frontline. Whether you’re a Fortune 500 company or a small nonprofit, consistent cybersecurity training can foil the simplest (and sometimes the deadliest) social engineering attacks.

5. **Strengthen Vendor Management**  
   Grill your third-party partners about their security posture. Do they patch regularly? Do they have a plan if an incident occurs? If not, send them brownies _and_ a stern lecture.

6. **Invest in Public-Private Collaboration**  
   Governments, private firms, and academia should share threat intelligence. It might feel like hugging it out with your competitor, but when a wave of sophisticated attacks rolls in, you’ll want every ally you can get.

---

## Concluding Thoughts

Our digital identity infrastructure is as fragile as it is vital—just ask the folks in El Salvador, Italy[^12], or any of the many places that suffered massive data breaches affecting millions. The key to staving off chaos is sustained vigilance, a willingness to invest in robust security frameworks, and a healthy dash of paranoia (okay, maybe just a pinch).

The future of digital infrastructure highlights the critical need for cross-sector collaboration, advanced identity verification, and proactive monitoring. In the meantime, keep your antivirus up to date, embrace multi-factor authentication like your life depends on it (it might!), and remember: Cybersecurity might be serious business, but we can still keep it lively, engaging, and—dare I say—fun to talk about.

Thanks for joining me on this whirlwind look at all things cyber. Stay sharp, update your software, and come back soon for more cybersecurity insights.

## References

[^1]: [National Health Service (NHS) Cyberattack (UK)](https://www.bbc.co.uk/news/articles/c9777v4m8zdo) – Ransomware attack on Synnovis impacting 400GB of stolen patient data, June 3, 2024.

[^2]: [LoanDepot Ransomware Attack (US)](https://investors.loandepot.com/news/corporate-and-financial-news/corporate-and-financial-news-details/2024/loanDepot-Provides-Update-on-Cyber-Incident/default.aspx) – Targeted mortgage lender, compromised 16.6 million customers (January 8, 2024).  

[^3]: [City of Columbus Ransomware Attack](https://www.cybersecuritydive.com/news/columbus-ohio-ransomware-500k/732154/) – Affected personal data of 55% of residents, July 2024.  

[^4]: [Mass Exploitation of Ivanti Zero-Day Vulnerabilities](https://cloud.google.com/blog/topics/threat-intelligence/investigating-ivanti-zero-day-exploitation/) – Early 2024, impacted government, military, and critical infrastructure. 

[^5]: [Snowflake Attack (June 2024)](https://cloud.google.com/blog/topics/threat-intelligence/unc5537-snowflake-data-theft-extortion) – Supply chain breach affecting Ticketmaster, Santander Bank, and AT&T.  

[^6]: [MOVEit Vulnerability Exploitation](https://www.biometricupdate.com/202411/amazon-delta-employee-pii-exposed-in-data-breaches) – Late 2024, exposed Amazon employee contact info and Delta Airlines user data.  

[^7]: [US Government Email Breach (Storm-0558)](https://www.microsoft.com/en-us/security/blog/2023/07/14/analysis-of-storm-0558-techniques-for-unauthorized-email-access/) – Began May 15, 2023, forging authentication tokens to access Microsoft and Azure AD accounts.  

[^8]: [Volt Typhoon Infiltration (January 31)](https://www.justice.gov/archives/opa/pr/us-government-disrupts-botnet-peoples-republic-china-used-conceal-hacking-critical) – Disrupted by the US DOJ, infiltration across communications, energy, transportation, and water sectors. 

[^9]: [Potential Breach of National Public Data (August 2024)](https://www.biometricupdate.com/202408/data-breach-exposes-3-billion-pii-records-class-action-suits-filed) – Public records data broker exposing personal info of possibly hundreds of millions.  

[^10]: [El Salvador National Data Breach](https://www.biometricupdate.com/202405/el-salvador-data-breach-includes-selfies-and-id-numbers-for-80-of-countrys-population) – Affecting 5.1 million people (80% of the country’s population) with facial photos, phone numbers, addresses, and DUIs.

[^11]: [Change HealthCare breach](https://techcrunch.com/2025/01/27/how-the-ransomware-attack-at-change-healthcare-went-down-a-timeline/) - A massive infiltration into the US healthcare payment provider led to 100 million individual data breach notices and forced a $22 million ransom payment.

[^12]: [InfoCert Italy Breach](https://www.biometricupdate.com/202501/italian-digital-identity-provider-suffers-data-breach-5-5m-customers-affected) - InfoCert reported a breach impacting 5.5 million customers, exposing phone numbers, email addresses, and other personal data.

---
