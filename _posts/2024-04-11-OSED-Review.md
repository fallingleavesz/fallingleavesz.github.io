---
title: OSED Review
date: 2024-04-11 00:00:00 -0400
categories: [Certs]
tags: [Exploit Development, Binary Exploitation, Reverse Engineering]
---



### Intro
Several days ago, I achieved my OSED certification. Given the scarcity of course reviews compared to OSWE, OSEP, or OSCP, I want to share my insights on the course materials, labs, resources, and exam for future reference.

OSED, which stands for [Windows User Mode Exploit Development](https://www.offsec.com/courses/exp-301/), is one of the three 300-level courses (EXP-301) offered by Offsec. It primarily focuses on Windows x86 architecture, but this knowledge can be easily applied to x64 platform.

By Offsec, 
> Windows User Mode Exploit Development (EXP-301) is a course that teaches learners the basics of modern exploit development. Despite being a fundamental course, it is at the 300 level because it relies on substantial knowledge of assembly and low level programming. It begins with basic buffer overflow attacks and builds into learning the skills needed to crack the critical security mitigations protecting enterprises



### Timeline & Background
1. 09/10/2023: Started
2. 04/04/2024: Took Exam
3. 04/08/2024: Passed

I didn't make any special preparations. Prior to taking OSED, I had the ability to read assembly code, understand memory layout, exploit basic stack overflows, and conduct simple reverse engineering using tools like IDA and GDB.


### Course Materials
Here is the [syllabus](https://www.offsec.com/courses/exp-301/download/syllabus) of OSED.

Offsec used real-world applications to illustrate the process of identifying vulnerabilities and developing corresponding exploits. It starts with "WinDbg and x86 Architecture" and vanilla "stack overflow", providing a refresher for those experienced  with binary security.

The chapter "Exploiting SEH Overflows" is exceptionally detailed. It provides an in-depth explanation of SEH Overflows and demonstrates how to trace the exception handler workflow to understand its mechanics thoroughly. It is rare to find other blogs that delve as deeply into SEH overflows as Offsec does.

The chapter "Egghunter" and "Create Custom Shellcode" are two of my favorites. Offsec introduces how to utilize egghunters to bypass space restrictions effectively and explains the creation of custom shellcode for greater flexibility. Moreover, Offsec doesn't hand over the code; instead, they demonstrate the entire process of building egghunters and shellcode from scratch. This include detailed explanations on debugging and making necessary changes when system changes occur.


After that come the three chapters: "Reverse Engineering", "DEP Bypass", and "ASLR Bypass". Offsec skillfully integrates these security mitigations bypass techniques with reverse engineering. This integration not only provides a thorough explanation of the bypass techniques but also demonstrates a strategic debugging approach. By following Offsec's detailed reverse engineering process, you'll gain a thorough understanding of how to approach a given program strategically, rather than simply sending 10000 'A' characters in the hopes of overwriting some EIP registers.


The last two chapters introduce format string vulnerabilities. I'm not particularly fond of these chapters. Although Offsec clearly explains the concept, the read and write primitives they introduce seem overly specific to that application. This specificity makes it hard for me to grasp the concepts fully and apply them in different contexts, which may steam from my own limitations in reverse engineering skills.


### Extra Miles and Labs

OSED offers three types of exercises: exercises, extra miles, and challenge labs. 
1. **Exercises** are small tasks listed at the end of each module, requiring you to reproduce what the course materials have shown, or to make simple modifications.
2. **Extra miles** are more difficult than regular exercises and not required to learn the material. They occur only at the end of each chapter and are chapter-specific.
3. There are only three **challenge labs**, which require comprehensive use of the techniques you've learned throughout the course.

I highly recommend to spend more time on extra miles. Personally, I completed all of the extra miles except for those in the reverse engineering chapter, as they were too open-ended. These exercises provide more practical experience and helped me deeply understand the course materials.

Take the DEP bypass for example. The course materials demonstrate how to use `rp++` to generate ROP gadgets and formulate the entire ROP chain to execute the shellcode. However, they do not explain why these particular gadgets were chosen and why they were assembled in this specific way rather than another. This reasoning process is something you must go through personally. 

By solving the extra miles, you have to walk through and think through the whole process to build the ROP chain. You'll gradually identify what types of gadgets are necessary for building a ROP chain, discover alternatives that might achieve the same functionality if the ideal gadget isn't available, and learn how to effectively assemble these gadgets. By practice, you'll eventually become more comfortable with applying these techniques. I would say there is a significant difference between understanding and mastery, especially in a practical field like binary exploitation.

Regarding the labs, I would say they are more like simulations of real-life exploit development rather than exam-style scenarios. While bypassing security mitigations in the labs is straightforward, locating the vulnerability is the most challenging part. It requires extensive reverse engineering skills or creative problem-solving, since it will significantly influence how you approach the challenge—why one path may be preferable to another. Therefore, even though I solved the challenges with the help of hints, I can’t convince myself why going this way rather than the other, likely due to my lack of proficiency in reverse engineering and limited experiences. 

Nevertheless, I fully understand that in reality, finding vulnerabilities is much harder and time-consuming than developing the exploit. 



### Resources
- [nop](https://github.com/nop-tech/OSED) has done a remarkable jobs sharing his lists for useful blogs for each chapter. It covers resources from x86 assembly, windbg cheatsheet to format string attacks.
- [Corelan Exploit writing tutorial](https://www.corelan.be/index.php/search/exploit+writing+tutorial+part+1/) is also an execellent resource that walks through exploiting stack overflow, SEH, egghunters, and more. It cover similar topics to those taught in OSED, making it a valuable supplementary resources to strenghten your understanding.
- **EXP-100** covers exploit development essentials, with the section on PE file format being particularly helpful.


### Exam
The exam lasts 48 hours, and you need to solve at least two out of the three given challenges to pass. The time is adequate, so there is no need to worry about running out of time.

I started my exam at 9pm on Friday. However, I failed to solve any of the three challengese within the first 24 hours. I was stuck on the last step of the first challenge and had no idea how to approach the third one at all. Around 25 hours, I finally solved the first challenge in an unexpected way, which, of course, I cannot disclose.

The second challenge was more straightforward. However, a mistake in failing to align the stack pointer cost me an additional five hours and kept giving weird bugs. Eventually, around 43 hours after starting, I resolved the second challenge.

Despite the challenges and mistakes I encountered during the exam, I would say the OSED exam is very straightforward. There aren't many rabbit holes, at least for the first two challenges. If you have a solid understanding of the course materials and have completed most of the extra mile exercises to practice your skills, it should be easy for you to pass OSED.

Honestly, writing the report was the most taxing part of the OSED exam for me. I ended up writing a nearly 100-page report. It's much easier to formulate these thoughts during the exam, thanks to the extensive exercises and time spent studying the materials. However, putting all of the thought into the report is a grueling process. Nonetheless, I spent about 10-13 hours writing and then submitted the report.

One day later, I received an email saying I had passed the exam. So happy ending.

![Certs](/assets/img/posts/2-OSED-Review/1-Cert.png)



### Conclusion
In conclusion, OSED provides a solid introduction of binary exploitation techniques and reverse engineering tricks. The course materials are well-documented and extra miles/labs are thoughtfully designed. I learned a lot and deepened my understanding of binary security through this course.