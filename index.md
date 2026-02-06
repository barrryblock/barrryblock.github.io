---
title: Dev → Sec
layout: default
---

<div class="content-container">
  <div class="content-box">
    <h2>About Me</h2>
    <p>
        I am <strong>John Prasad</strong>, a <strong>Cyber Security Researcher</strong> and <strong>Engineer</strong> specialising in the intersection of <strong>Threat Intelligence</strong>, <strong>Detection Engineering</strong>, and <strong>Cloud Security</strong>. With a career that evolved from <strong>Senior Software Engineering</strong> at CGI (Shell UK) to advanced research at the <strong>University of Warwick</strong>, I focus on building resilient, automated security architectures.
    </p>
    <p>
        My work spans developing <strong>scalable CTI pipelines</strong> using OpenStack and OpenCTI, engineering <strong>DevSecOps</strong> workflows with "Shift-Left" CI/CD principles, and researching <strong>Post-Quantum Cryptography</strong> for secure protocols. Whether I am hardening <strong>Kubernetes</strong> clusters or designing <strong>Zero Trust</strong> biometric systems, my goal is to translate complex raw data into actionable, high-fidelity defense strategies.
    </p>
    <p><a href="./about">Read More About Me</a></p>
  </div>
  
  <div class="content-box">
    <h2>Blog</h2>
    <p>In my blog, I will share insights on <strong>Cyber Threat Intelligence, Security Automation, Risk Mitigation</strong>, and <strong>emerging cybersecurity trends</strong>. Additionally, I have documented my journey through my <strong>MSc in Cyber Security Engineering</strong>, discussing the key modules I studied, my master's thesis, and the valuable lessons I learned throughout the program. I am writing about how I am running a comlicated HomeLab as well. Stay tuned for in-depth articles and technical explorations!</p>
    <p><a href="./blog">Read My Blog</a></p>
  </div>

</div>

<style>
  .content-container {
      display: flex;
      justify-content: space-between;
      gap: 20px;
      max-width: 1200px;
      margin: auto;
      padding: 20px;
  }

  .content-box {
      width: 48%;
  }

  /* Stack into one column on mobile */
  @media (max-width: 768px) {
      .content-container {
          flex-direction: column;
      }

      .content-box {
          width: 100%;
      }
  }
</style>
