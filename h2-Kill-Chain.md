# h2 Kill Chain

Text in *cursive* are comments by the author

## Task X Read and summarize [Hutchins et al 2011: Intelligence-Driven Computer Network Defense Informed by Analysis of Adversary Campaigns and Intrusion Kill Chains](https://lockheedmartin.com/content/dam/lockheed-martin/rms/documents/cyber/LM-White-Paper-Intel-Driven-Defense.pdf)

- At the time of creation of the paper a change in the goals and sophistication of attacks had been noticed
- Advanced Persistent Threats (APT) were recognised as its own category - These are describe by being well resourced and trained adversaries that have extended time periods available to reach their objectives
- Term "Kill Chain" from U.S. military doctrine (US Department Of Defense 2007)
- Describes process to attack or destroy targets in a traditional military context
- Described as "chain" because any one link of the process being deficient can break the entire thing
- The term "intrusion kill chain" expands from that and focuses specifically on intrusions into computers and computer networks
- The 7 steps of the intrusion kill chain are: reconnaissance, weaponization, delivery, exploitation, installation, Command and Control, and taking actions on objectives
- Each step forms and important piece without which the whole does not function or have the desired outcome
- Reconnaissance: This represents any research of technologies and targets, identifying key assets, selecting targets and similar activities.
- Weaponization: Exploiting a tool to deliver a remote access trojan. Often PDF's or other advanced text files are used for this step. *probably because they more easily seem inconspicous and titles are trusted blindly*
- Delivery: The actual act of delivering said payload to the target often through email attachments, websites or USB media *at least in the years 2004-2010. By 2026 especially USB sticks might have lost relevancy in this regards*
- Exploitation: Once the package has been delivered it is time in this step to exploit a vulnarability often in the operating system or an application. Sometimes users themselves are exploited too
- Installation: After the vulnarability was successfully exploited and code installation is possible it is time to install the remote access trojan
- Command and Control (C2): To be able to follow through on the next step a host must usually connect to an external server that the attacker controlls. In cases of APT malware this happens after a manual trigger as they target specific systems. *In more general context for example in cases of Ransomware this happens often automatically*
- Actions on Objectives: After these 6 steps it is now time to actually take actions to reach the objectives defined in step one. Common objectives are: Data exfiltration, destruction of files, limiting access to data and using the initially attacked device as a starting point for further attacks on the network to move laterally to other sections and devices

## Task A - Tactics, tools and Procedures (https://attack.mitre.org/)

### Tactics

Tactics are generally the reason for choosing a specific technique or subtechnique. It answers the question "Why use this technique over another?" and describes the adversary's tactical goal. An example of a tactic is for example privilege escalation.
Privilege escelation techniques aim to exploit vulnarabilities that give an adversary more rights in a network or device than the most basic user has. 

### Technique and Subtechnique

Techniques are answering the question "How is this attack performed?". Usually meanining specific actions but described on a higher less detailed level. Subtechniques on the other hand describe the steps taking by adversaries in more details mentioning for example specific technologies. *This difference is may be made to be able to communicate more efficiently with different target audiences* An Example of a technique used for privilege escalation is abusing the elevation control mechanism itself to gain more access than originally provided. A subtechnique within that is abusing the setuid and setgid bits within Linux and MacOS. 

### Procedure

Between techniques, subtechniques and procedures, prodcedures go into the most technical detail of an adversary's actions. As they often decribe behaviour "in-the-wild", they can cover several techniques or subtechniques. While techniques and subtechniques are usually theoretical in nature, procedures are based on observed behaviour by adversary's. *This could also be described as Tactics and (sub)techniques describing the "Why?" and "How?", while procedures describe the "What?"* An example of a procedure abusing the above mentioned subtechnique is the tool Examarel for Linux, which uses setuid to execute its payload with high privileges
