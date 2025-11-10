

## 📋 Submission Information

**Name:** Kaan Kadir Aluçlu
**Email:** kaankadiraluclu@gmail.com
**LinkedIn:** [https://linkedin.com/in/kaankadiraluclu/](https://linkedin.com/in/kaankadiraluclu/)
**Submission Date:** 2025-11-10

-----

## ✅ Deliverables Checklist

Please confirm you've included all required items:

  - [X] **Report** (PDF, max 5 pages)
  - [X] Section 1: Incident Analysis
  - [X] Section 2: Architecture Review
  - [X] Section 3: Response & Remediation
  

  - [X] **Video Presentation** (10-15 minutes)
      - [X] Link provided in `video_link.md`
      - [X] Video is accessible (tested in incognito)
      - [X] Duration is within guidelines

  - [X] **File Structure**

<!-- end list -->

```
  submissions/
  ├──   [Analysis Report.pdf] 
[Kaan_Kadir_Aluçlu_Report.pdf](https://github.com/user-attachments/files/23444591/Kaan_Kadir_Aluclu_Report.pdf)
  _├── [video_link.md]
[video_link.md](https://github.com/user-attachments/files/23444594/video_link.md)
  └── notes.md (optional)


```


-----

## 📊 Self-Assessment

**Time spent on this lab:** Approximately 55-60 minutes (includes preparing video and report)

**Tools used:**

  - Log analysis: Terminal (cat, grep), Kate (Text Editor)
  - Document review: Okular
  - Diagrams: draw.io
  - Video recording: N/A

**Confidence level:**

  - [X] Very confident in my analysis
  - [ ] Confident but some uncertainties
  - [ ] Attempted my best with available knowledge

-----

## 🎯 Brief Summary (2-3 sentences)

My approach involved a chronological correlation of API, Web, and WAF logs to trace the attacker's activity. The key finding was a multi-vector attack using a single stolen token (user_1523). The attacker first exploited a critical IDOR in the API to exfiltrate user portfolios, then pivoted to the web app, bypassed the WAF with an obfuscated SQLi, and exported a large CSV database.

-----

## 🔍 Key Findings Highlight

**Main attack vectors identified:**

1.  API Broken Access Control (IDOR) via stolen JWT (user_1523)
2.  Web SQL Injection (CWE-89) with WAF Bypass
3.  Phishing (Observed campaign, likely initial vector for token theft)

**Most critical vulnerability:**
CWE-639: Broken Access Control (IDOR) on the /api/v1/portfolio/ endpoint. This allowed any authenticated user to view any other user's portfolio data by simply iterating the ID in the URL, indicating a total lack of server-side authorization.

**Top recommendation:**
Implement server-side authorization checks on all API endpoints. The logic must validate that the authenticated user's ID (from the JWT) matches the requested resource's owner ID. For the web, immediately implement parameterized queries to mitigate all SQLi.

-----

## 💭 Challenges & Learnings

**What was most challenging?**
Correlating the two distinct attack phases (the 06:45 API attack and the 09:23 Web attack) to the same attacker and user identity (user_1523). It was also a good challenge to identify the specific WAF bypass payload (`/*!50000OR*/`) and see why the WAF rule failed to block it.

**What did you learn?**
I learned how a single point of failure (one stolen token) can be leveraged to compromise multiple, differently-vulnerable systems. It clearly demonstrates that application-layer security (like proper authorization) is critical and cannot be replaced by network-layer defenses like a WAF, which can be misconfigured or bypassed.

**What would you do differently?**
Initially, I might have treated the API and Web incidents as separate. Next time, I would immediately cross-reference the user (1523) and IP (203.0.113.45) across all available log sources (API, Web, WAF, Email) to build a unified timeline faster.

-----

## 📝 Additional Notes *(optional)*

The analysis was performed entirely using standard Linux/KDE tools. Log files were filtered and cross-referenced using cat and grep in the terminal. Kate and a notepad were used for isolating and documenting suspicious log entries. Okular was used to review the provided PDF documentation. No automated SIEM or log analysis platforms were used.

Finally, please excuse any hesitation or stumbling in my spoken English in the video. It is not a language I get to practice speaking in my daily life, but I am fully confident in the technical analysis itself.

-----

## ⚖️ Declaration

I declare that:

  - [X] This work is entirely my own
  - [X] I have not copied from other submissions or answer keys
  - [X] I have not modified the provided log files
  - [X] All sources and tools are properly attributed
  - [X] I understand plagiarism results in disqualification

**Signature:** Kaan Kadir Aluçlu
**Date:** 2025-11-10

-----

## 🚀 Ready for Review

By submitting this PR, I confirm that my work is complete and ready for evaluation.

-----

*Thank you for your submission\! Our team will review it within 1 week.*
