---
title: OSCP Review
date: 2023-07-11 00:00:00
categories: [Certs]
tags: [Penetration Testing, Priviledge Escalation, Active Directory]
img_path: /assets/img/posts/1-OSCP-Review/
---

### Intro
I have recently received my OSCP certification, and would like to share my thoughts on the course materials and my learning process.

OSCP, which stands for [Offensive Security Experienced Penetration Tester](https://www.offsec.com/courses/pen-200/?utm_campaign=Google-Ads_Brand_PPC_PWK_2020_Update_NAM=&utm_medium=cpc=&utm_source=google=&utm_source=adwords&utm_term=kwd=oscp:cid-9248778671:aud-849470793483:kwd-314572348942:dev-c:mt-e&utm_campaign=Brand_PPC_PWK_2020_Update_USA&utm_medium=ppc&utm_content=crid=658310795943&hsa_mt=e&hsa_ad=658310795943&hsa_net=adwords&hsa_src=g&hsa_kw=oscp&hsa_tgt=aud-849470793483:kwd-314572348942&hsa_cam=9248778671&hsa_acc=7794287291&hsa_ver=3&hsa_grp=92741699943&gad_source=1&gclid=CjwKCAjwuJ2xBhA3EiwAMVjkVJaMIFzNpQZ1OXLa4sg7jB7VZ8As4WV5RToHbZRBq7ATdKdlmDKfiRoCZQYQAvD_BwE), is an intermediate-level course (PEN-200) provided by Offsec. It is arguably one of the most well-known certifications in the field of penetration testing and enjoys a strong reputation among recruiters.




### TimeLine
1. 02/23/2024: started the course
2. 07/02/2024: took the exam
3. 07/09/2024: receive the badge

### Background
As a bit of background for those who don't know, I'm a master student stuyding cyber security. However, I learned statistics and economics during my undergraduate. 

I spent initial four months of my master learning the basics of security on TryHackMe. Following that, I spent two more months familarizing myself with common web application vulnerabilities on PortSwigger Web Academy. After that, I started my OSCP journey.


### Course Material
When I was studying for the OSCP, the course underwent a significant update at the end of March 2023. It removed the buffer overflow section, and made numerous changes to the remaining chapters. I liked the updated course material so much because it was much better organized, which made it more understandable and logical to me.

[OSCP Syllabus](https://www.offsec.com/courses/pen-200/download/syllabus)

Web application attacks in the OSCP curriculum serve more as a brief demonstration of common web vulnerabilities rather than providing detailed instructions on identifying and exploiting them under different conditions, where PortSwigger Web Academy has done a great job. This is likely because OSCP focuses more on penetration testing as a whole, rather than specifically on web application vulnerabilities.

Windows & Linux privilege escalation provides a good introduction to the potential attack vectors that can lead to elevated privileges. It might appear a bit overwhelming at first glance, but once you document all the possible aspects of privilege escalation techniques, everything becomse much clearer.

Active Directory attacks are a major focus in the OSCP course. Offsec provides detailed explanations of Active Directory's authentication processes, common attack vectors, and strategies for lateral movement. However, this might be the most challenging module for those unfamiliar with Active Directory, like me. Personally, I had to review these modules several times, read additional blogs, and watch videos to fully grasp the concepts.

Among the various modules covered, port redirection and tunneling is one of my favorite. It covers techniques that allow you to extend your reach within a network. Often is the case you might gain a foothold in an internal network where directly executing scripts from your attack machine is not feasible. Moving scripts and tools to the foothold could produce a lot of noise. That's where port redirection and tunneling come into play——these techniques allow you to quietly bridge the gap between your attack machine and the internal targets.


### Labs
OSCP offers six challenges: challenge 1, 2, 3——each featuring a set of network machines connected through Active Directory; OSCP A, B, C——each providing an OSCP-like experience. These consists of three standalone machines along with an Active Directory set.

The labs are excellent resources to refine your skills and review what you have learned. I highly recommend completing Challenges 1, 2, and OSCP A, B, C at a minimum. Challenge 3 is not required, as it is more difficult than the exam itself.

I also suggest that you should develop your OSCP methodology or playbook when solving challenges, as it will be invaluable during your exam. As a penetration tester, it's crucial to have a systematic approach to different scenarios, clearly outlining your methods for performing vulnerability assessments, executing privilege escalation, and handling other critical tasks.


### Tools / Resources
While the course materials provided by Offsec are already well-documented and adequate for both the labs and exams, I've also utilized some external resources and tools during my exam preparation that might be helpful.

Resoureces
1. **Reddit r/oscp**: Every day, there are blogs sharing experiences of either passing or failing the exam.  These posts can be a great learning tool, allowing you to adopt successful strategies and avoid common pitfalls. Contributors also frequently share new tools, resources, and exam tips.
2. **HTB AD machine**: Although I didn’t personally solve the machines, I watched Ippsec's videos on `Active`, `Forest`, `Reel`, `Sizzle`, and `Sauna` AD boxes to gain more confidence in handling Active Directory.


Tools
1. [Tmux](https://github.com/tmux/tmux/wiki): a terminal multiplexer.
2. [Ligolo ng](https://github.com/nicocha30/ligolo-ng): an advanced, yet simple, tunneling/pivoting tool that uses a TUN interface, much better than `Chisel`.


### The Exam
The OSCP exam spans for 24 hours. I began my exam at 5 AM, planning to tackle the Active Directory set first, followed by the standalone machines. Since points for the AD set are awarded only if you fully exploit the domain chain, in order to pass the exam, you can either complete the AD set and capture two additional flags, or solve all three standalone machines. The former option is generally less challenging than the latter.

However, after three hours of enumerating the AD, I had yet to locate a vulnerability that would give me a foothold. Deciding to shift gears, I moved on to the standalone machines. Fortunately, the first standalone machine was relatively easy, and I gained root access within an hour. While documenting the process with screenshots, my VM unexpectedly crashed. The repeated hanging issues after restarting cost me another hour and a half to resolve. Although I was becoming nervous, I reminded myself to stay calm, focusing on the exam itself, considering its 24-hour duration.

Four hours later, I had rooted the second standalone machine. By then, I had had three cups of coffee and taken two cold showers. After a short break, I began working on the last standalone machine. Five hours later, around 8 PM, which marked 15 hours into the exam, I successfully rooted the last machine. This gave me enough points to pass the OSCP, although the path I took was unexpected.

After spending an additional five hours on the AD set without success, I decided to end the exam. The following day, I submitted my report and received confirmation from Offensive Security six days later that I had passed.

![Cert](/assets/img/posts/1-OSCP-Review/OSCP_CERT_Email.png)


### Conclusion
It has been an incredible journey. Just ten months ago, I had barely any knowledge about security. Now, I've successfully obtained the OSCP certification, passing it on my first attempt. I am truly grateful for this experience. Not only have I learned a plethora of fascinating hacking techniques, but I've also developed a resilient mentality in navigating various challenges along the way. Perhaps that is also part of the learning process.

As mentioned in *The Little Prince*, "It is the time you have wasted for your rose that makes your rose so important". The time and effort I invested, along with the challenges I faced in obtaining the OSCP certification, are what make this journey particularly cherished.

