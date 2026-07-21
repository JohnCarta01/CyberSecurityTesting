# Introduction to Cyber Security Testing, week 1

## Task 3

After reading the paper linked in the task description, this is my essay:

The Importance of Thinking Models and Technical Expertise in Cybersecurity Testing
Cybersecurity testing is crucial for modern software development. Even though automated security tools are becoming better and better, the effectiveness of testing still relies on human expertise and thinking models. This essay explores the role of thinking models and domain-specific expertise in security testing, highlighting why automation alone cannot fully replace human experience.

A fundamental aspect of security testing is the mental models used by testers to identify vulnerabilities. The paper "Understanding Hackers’ Work: An Empirical Study of Offensive Security Practitioners" identifies two primary mental models for vulnerability identification: finding known vulnerabilities and hunting for new ones.
- Known vulnerabilities can be mitigated through rigorous security practices - adherence to security standards. Despite these efforts, vulnerabilities continue to exist due to human error, better attack techniques, and legacy systems that cannot be easily updated.
- And if known vulnerabilities can be detected through automated tools and databases, new vulnerabilities emerge from unique interactions within a system: hunting for new vulnerabilities requires human testers’ creativity and lateral thinking. Here is where the limitations of automation in cybersecurity testing emerge the most. 

Automation excels at systematic checks, such as scanning for outdated software, identifying misconfigurations, and testing for common exploits. However, it lacks the ability to intuitively assess software behavior and reason through complex attack chains. \
Unlike SQL injections or buffer overflows - detectable through predefined patterns - many vulnerabilities arise from the way the software processes data: it’s necessary to understand how the application works, and this is done thanks to mental models that are built with the experience.
Also, it’s often important to have a deep experience into a specific ‘business area’ / a specific domain. Even if this can come with kind of disadvantages sometimes.

The paper suggests that security professionals tend to find vulnerabilities in areas they are familiar with, sometimes at the cost of overlooking other potential ones. This phenomenon, described as "tunnel vision”, occurs when expertise in one domain “blinds a tester” to threats emerging from different perspectives. While expertise enhances a tester’s ability to spot vulnerabilities, it can limit its “instinct for exploration”. \
To counteract this limitation, testing teams and interdisciplinary collaboration are essential. Cross-domain knowledge sharing, regular interaction between different security disciplines, and red team exercises help testers develop a better security perspective.

The paper references the "Red Queen’s Race”, a metaphor from evolutionary theory that stands for: security professionals should constantly evolve to keep pace with attackers. Cybersecurity is a continuous battle where new attack methodologies are implemented and defenders must adapt. Security measures can easily become obsolete, as attackers continually renew their strategies to bypass existing defense measures. \
This dynamic nature of security underscores why thinking models and expertise remain irreplaceable. Security professionals must engage in continuous learning and hands-on practice to stay ahead of attackers. The effectiveness of cybersecurity testing is not just about technical skills, but also the ability to anticipate possible new threats.

A comprehensive cybersecurity approach involves threat modeling: a process of identifying assets, assessing potential threats, mapping threats to vulnerabilities, and implementing mitigation strategies. \
Effective threat modeling requires a deep understanding of the system architecture, attack surfaces, and what design decisions imply about security. Without technical expertise and a good thinking model, it easily becomes superficial and ineffective. \
Automation can assist in threat modeling, but it cannot replace the judgment required to predict unexpected attacks. Human security experts must interpret results, contextualize findings, and refine models based on real-world attack scenarios. This process requires experience, intuition, and adaptability: things that automated tools don’t and - at the moment - can’t have.

To summarize, while automation plays a vital role for efficiency and known vulnerabilities, it cannot replace the intuition and creativity of human testers. Thanks to thinking models, professionals can identify and exploit vulnerabilities in ways that automated tools cannot.
And about organizations, they need interdisciplinary collaboration, continuous learning, and red team exercise. A balanced approach, integrating automation with human expertise, is essential to staying ahead in the "Red Queen’s Race”.

Experts are necessary. Automations tools are… tools.
