---
title: OffSec Experienced Penetration Tester (OSEP) Review
date: 2024-09-06 00:00:00 -0400
categories: [Certs]
tags: [Penetration Testing, Antivirus Evasion, Active Directory Exploitation]
---

## OSEP Review 2024

### Introduction
The [Offensive Security Experienced Penetration Tester (OSEP)](https://www.offsec.com/courses/pen-300/) is an advanced penetration testing certification offered by OffSec, with a strong focus on client-side phishing, antivirus evasion, and Active Directory exploitation. In this blog, I will share my personal experience with the OSEP course, discussing my thoughts on the learning materials, labs, exam, and my overall impressions of the certification.

### Course Materials
OSEP places a significant focus on client-side phishing, illustrating how to customize code to bypass antivirus detection and execute it even if the host has application whitelist enforced, which is my favorite part of OSEP. I list the [syllabus](chrome-extension://efaidnbmnnnibpcajpcglclefindmkaj/https://manage.offsec.com/app/uploads/2023/01/PEN300-Syllabus-Google-Docs.pdf) here. 

The course begins with client-side code execution using a Microsoft Word macro, which calls Win32 APIs from VBA to execute the shellcode. However, since the shellcode is stored in the macro and saved on disk, it is at risk of being detected by antivirus software. To overcome this challenge, it later implements a PowerShell shellcode runner that executes entirely in memory and updated the Word macro to invoke the PowerShell script instead. The course also offers a detailed walkthrough on building a similar shellcode runner in C#, and how to translate the C# code into JScript, which can bypass certain security controls in specific scenarios.

To mess around with both heuristic and signature-based AV, the course introduces several techniques, including sleep timers, non-emulated APIs, shellcode encryption, and obfuscation. It revisits the Word macro and C# code we built earlier, and with these techniques applied, you're able to bypass 25 out of 26 antivirus engines on AntiScan.Me—pretty cool! Additionally, the course dives into challenges posed by Antimalware Scan Interface (AMSI), application whitelisting (AppLocker) and Constrained Language Mode (CLM).

By this point, you'll have a comprehensive understanding of common security defense mechanisms (AV, AMSI, CLM, AppLocker, etc.) and their weakness. You'll be able to combine these concepts to create custom shellcode and build attack chains that bypass these defenses.

For the remaining half of the content, I found it less systematic and not as engaging as the earlier sections. It covers common attack surfaces for DevOps tools like Ansible and Artifactory. It also revisits Active Directory exploitation, similar to what we covered in OSCP, introducing the three types of Kerberos delegation (unconstrained, constrained, and resource-based) and exploring inter- and intra-forest trust exploitation. Additionally, it dives into MSSQL attacks, showing how misconfigurations with impersonation and linked servers can lead to remote code execution. While it's good to know these topics, it feels like something you could just Google—like searching "Kerberos delegation exploitation" when you see that result in BloodHound and reading some blogs about it.


### Labs
OSEP offers six lab sets. The first three are small Active Directory domains, while the last three grow in size and complexity, featuring multiple domains. These labs provide a great environment to refine your client-side phishing and antivirus bypass techniques, and practice everything you've learned throughout the course. Additionally, by checking offsec OSEP channel and forum, you'll discover some useful open-source tools or scripts commonly used by other OSEPers, which can help streamline your pentest, saving you from having to implement everything from scratch. It took me about five weeks to complete, and it’s excellent preparation for the exam.


### Exams
The exam is a large active directory environment and the goal is to find a secret.txt in the core domain. There are two paths to achieve the objective. To pass the exam, you can either obtain the secret.txt or find 10 flags within the internal network, as proof of gaining a foothold or compromising the hosts.

During my first exam attempt, I captured three flags within the first six hours, but after that, I was completely stuck until the exam ended. I found some information indicating a potential email phishing point. However, despite trying everything I could think of, I never received the reverse shell, even though the same code had worked perfectly in the labs. It was frustrating because I couldn’t tell whether I was using the wrong method or if my code was still being detected by the antivirus. It seems OffSec had added extra tricks to make the client-side exploitation part less straightforward than the one in the labs, but unfortunately, I fail to figure it out. As a result, I failed my first attempt.

I scheduled my second attempt 20 days later and, unexpectedly, got the same exam set. I felt pretty down, as I still didn’t know what I had missed in the first attempt, which made me think I might fail again. However, after a lot of trial and error, I realized there was something I had overlooked during my first try. It turns out there were two vulnerabilities in one application, each leading to different exploitation path. I had assumed there was only one way to exploit the app, based on my experience with the labs. What a stupid mental set.

After 24 hours, I secured 10 flags, but I still couldn’t get the email phishing to work. Eventually, I wrapped up the exam and spent a few hours writing the report. Five days after submitting the report, I got an email congratulating me on passing.
![Certs](/assets/img/posts/3-OSEP-Review/1-Cert.png)

To be honest, even though I passed the exam, I don't like how this exam is designed, becuase of the issues I've mentioned above. While I admit that some might argue these situations could happen in real-life pentesting—or even be tougher—I believe for certs, there are better ways to design exams that test both the "try harder" mentality and mastery of the course material. Unlike OSCP you have three standalones machines, so if you stuck somewhere, you still get the chance to exploit others and grab enough points. But for OSEP, there are only two paths of exploitation, if you are stuck in one path, even if the hosts after that are simple, you don't have the chance to exploit these and you're likely not able to get enough flags to pass it. Anyway, I'm glad that I passed in the end though it was such a brutal experience.


### Resources
While you may have already seen the following resouces in others' OSEP reviews, I list the ones that I use and think are the most useful as belows:
- Knowledge Base - [Experienced-Pentester-OSEP](https://github.com/nullg0re/Experienced-Pentester-OSEP)
- OSEP Scripts - [OSEP Code Snippets](https://github.com/chvancooten/OSEP-Code-Snippets)

While I didn't complete some recommended HTB pro labs like Cybernetics, I do agree those are good resources for preparing OSEP, not just because they might be somewhat similar, but also because I believe passing OSEP requires a lot of accumulation over time, which can be gained either from practical work experience or from hands-on lab environments.

### Conclusion
All in all, OSEP has its pros and cons. I enjoyed the antivirus evasion techniques and was impressed by the level of detail OffSec dives into, but I wasn’t really into the exam or some of the other materials.

If you're interested in antivirus evasion, it’s worth considering, as it offers a solid introduction to common security controls you might encounter. However, if I could roll back the clock a few months, I probably wouldn’t choose OSEP, since aside from the antivirus part, it’s kind of similar to OSCP, and you can learn much of the material on your own.

