Experiment 8: Mapping Threats with MITRE ATT&CK
Aim
To analyze a sample cyberattack scenario, map the identified attack
techniques to the MITRE ATT&CK framework, and recommend suitable
security mitigations.
Overview
MITRE ATT&CK is a knowledge base of adversary tactics and techniques
based on observed cyberattack behavior. It helps security learners and
analysts understand how attacks may progress and organize their findings
using a common framework.

In this practical, the MITRE ATT&CK website, Enterprise Matrix,
technique pages, and ATT&CK Navigator were explored.
Tools and Requirements
- Computer with internet access
- Web browser
- MITRE ATT&CK website
- MITRE ATT&CK
  Navigator
Practical Work
1. Explore the MITRE ATT&CK website
Open https://attack.mitre.org/ and explore the framework and its
Enterprise ATT&CK resources.
2. Study Exploitation for Privilege Escalation
Open the Exploitation for Privilege Escalation technique page. Read
its description to understand how an attacker may exploit a software
vulnerability to obtain higher privileges.
3. Study Exploit Public-Facing Application
Open the Exploit Public-Facing Application technique page. Examine
how vulnerabilities in applications exposed to the internet may be
exploited to gain access to a system.
4. Explore the Enterprise ATT&CK Matrix
Open the Enterprise ATT&CK Matrix and observe how tactics and techniques
are organized. Tactics describe an attacker's objective, while
techniques describe how that objective may be achieved.
5. Explore ATT&CK Navigator
Open ATT&CK Navigator and examine its matrix-based view. Navigator can
be used to create and view layers for organizing or highlighting
techniques.
6. Observe the practical output
Review the terminal output captured during the practical. Record the
command and explain its output here only after confirming what was
executed; the screenshot alone does not establish the command or its
purpose.
Techniques Observed
  Technique name          ATT&CK ID               General purpose
  Exploitation for        T1068                   Exploiting a
Privilege Escalation                            vulnerability to gain
higher privileges
Exploit Public-Facing   T1190                   Exploiting a
Application                                     vulnerability in an
internet-facing
application
The technique names and IDs above identify the two technique pages
shown in the practical screenshots. They should not be treated as
proof that an attack was executed.

Suggested Security Mitigations
- Keep operating systems, applications, and exposed services updated.
- Fix known vulnerabilities in internet-facing applications.
- Limit user and service permissions according to the principle of
  least privilege.
- Monitor systems for unusual privilege changes and suspicious
  activity.
- Use endpoint protection and centralized logging where available.
- Perform regular vulnerability assessments and security reviews.
Screenshots
Add the screenshots captured during the practical in this order:
1. MITRE ATT&CK homepage.
2. Exploitation for Privilege Escalation technique page.
3. Exploit Public-Facing Application technique page.
4. Enterprise ATT&CK Matrix.
5. ATT&CK Navigator.
6. Terminal output from the practical.
Suggested folder structure:
Experiment-8-MITRE-ATTACK/
├── README.md
└── screenshots/
    ├── 01-mitre-homepage.png
    ├── 02-privilege-escalation.png
    ├── 03-public-facing-application.png
    ├── 04-enterprise-matrix.png
    ├── 05-attack-navigator.png
    └── 06-terminal-output.png
Replace the example filenames with the actual screenshot filenames in
your repository. To display an image in this README, use Markdown image
syntax, for example:
![MITRE ATT&CK homepage](screenshots/01-mitre-homepage.png)
Result
The MITRE ATT&CK website, two technique pages, the Enterprise ATT&CK
Matrix, and ATT&CK Navigator were explored. The observed techniques were
identified by their ATT&CK names and IDs, and relevant defensive
measures were listed.
Conclusion
This practical introduced the use of the MITRE ATT&CK framework for
understanding and classifying adversary behavior. It demonstrated how
technique pages and the Enterprise Matrix can help organize attack
knowledge and support security analysis.
