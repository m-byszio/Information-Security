#h1 Should Tero wear a helmet?

## Task X

### Threat Modeiling manifesto (https://www.threatmodelingmanifesto.org/)

- Four key questions: What are we working on? What can go wrong? What are we doing about it? Did we do a good enough job?
- Threat modeling is about recognizing what could go wrong in a system and what could be done to prevent this event from happening
- Threat modeling is for everyone
- In the Threat Modeling Manifesto Values are relative and Principles are fixed
- Threat modeling is in the service of the companies processes and structure not the other way around
- Beneficial patterns: Systematic Approach, Informed Creativity, Varied Viewpoints, Useful Toolkit and Theory into Practice

### Worlds Shortest Threat Modeling Course
- Adam Shostack wrote a book on Threat Modeling and is mentioned in the OWASP Threat Modeling Cheat Sheet
- Threat modeling is done to anticipate problems when its cheapest to deal with them and changes can be made quickly
- Collaboration during threat modeling is crucial to answer the question "What are we working on?"
- Sketching allows collaborators to see what is in our heads so they can engage with and respond to it. This allows answering the question "What could go wrong?"
- A document of record can be important to fulfil compliance requirements
- Data flow diagrams are simple to draw and easy to use
- Threats tend to follow data
- 4 Symbols: Sharp corners for things outside of our control aka external entities, Ovals or circles for things inside of our control aka internal entities, Drums for data storage, Dotted lines for trust boundaries to differentiate control by different entities, Arrows for data flow
- The question "What can go wrong?" gives a space to already existing concerns
- STRIDE as a structure to answer the question "What can go wrong?"
- STRIDE happens in all kinds of systems
- Tracking your work is crucial for threat modeling so that each part of your work is not forgotten about
- Risk management targets a subset of the answers to the question "What are we going to do about it?"
- Asking "Did we do a good enough job?" lets you understand if your work is actually done

### OWASP Threat Modeling Cheat Sheet (https://cheatsheetseries.owasp.org/cheatsheets/Threat_Modeling_Cheat_Sheet.html, 20.01.2026)
- "Threat modeling is an important concept for modern application developers to understand."
- "Threat modeling analyzes a system from an adversarial perspective, focusing on ways in which an attacker can exploit a system."
- It is not something that is performed once and never again
- According to OWASP advantages of threat modeling are that it identifies risks early on, increases security awareness and improves visibility into systems through evaltuation of said system
- No universally accepted standard for threat modeling, no "right" answer
- **System modeling** is about answering the question "What are we building?". System modeling creates an understanding of the system. Data flow diagrams (DFD) are the most common approach
- DFDs visualize system interactions with data and other entities
- Depending on the complexity of the system multiple DFDs might be required
- Brainstorming is another approach with advantages in certain situations, as it ensures engagement from all participant and a common understanding of the whole system
- "It is important that the solution provides a clear view of trust boundaries, data flows, data stores, processes, and the external entities which may interact with the system."
- Modern solutions tend to be cloud based and traditional models like DFD need adjustment to be usable for cloud architectures
- In the context of the distributed nature and shares responsibility model of cloud architectures the following should be accounted for: Additional components, security controls that might be outside of your own responibility, the dynamic nature of containerised infrastructure and the increased compliance need
- **Threat Identification** deals with the question "What could go wrong?"
- STRIDE is a popular technique. It stands for **S**poofing **T**ampering **R**epudiation **I**nformation disclosure **D**enial of Service **E**levation of Privileges
- It proivides a structure to the question "What could go wrong?"
- Identification also include prioritization
- **Response** and Mitigations deal with the question "What are we going to do about it?"
- Adam Shostack offers these options: Mitigate, Eliminate, Transfer and Accept
- Depending on the complexity of the system these can apply on a categorical or and individual level
- If the choice is based on a threat category then the "solution" is applied to all threats within that category
- If the choice is based on each individual threat, the "solution" is also applied to each individual threat only
- **Review and Validation** deals with the question of "Did we do a good enough job?"
- All stakeholders must be involved in this review process to ensure that a wholistic viewpoint is reached

   
### Darknet Diaries Loteria

- The lottery of Puerto Rico is losing lots of money every month
- When audited no foul play was found
- Auditor went undercover to investigate
- Found lots of secondary problems like the financial records being stored in the ground floor where they could flood
- Found a room with an old computer that he could access freely as local admin to try to access the network
- Maps the network to find out what devices are on it
- Found a vulnarable webserver through which he could access the network from the outside
- Monitored the network waiting for the threat actors to do something
- They found an insider threat that was changing database entries to get higher pay outs on winning lottery tickets
- Through this process they uncovered a much larger cartel operation
- After that they were taken off the Island by the FBI

## Task a) Security Hygiene

In this text I try to find security practices that everyone should follow. The first thing that should always be mentioned is to use strong passwords and multi factor authentication as these two in combination can already prevent a large number of threats.
The next thing that anyone that uses computers should keep in mind is the source of the files that they are using. A file downloaded from an unconfirmed source or from a unknown USB stick can pose major risks to any system. 
Another easy thing that anyone can do to prevent unauthorized access to your files is to lock your computer when you leave your desk and never leave your devices unsupervised when you are in a public space.
If you regularly work in a public space you should use a privacy filter to reduce the angle at which your screen can be viewed so that an outsider cannot easily read your screen or take pictures of it. 

## Task b) Make-belief boogie-man

### The company 

Disclaimer: Details of this company were created with ChatGPT model 5.2 
Initial prompt: I am doing a course on information security. For that I need to create a threat model for an imaginary company as a homework. Please give me 3 ideas for a company that is suitable but not too complex for this exercise 
Link to the chat: https://chatgpt.com/share/696fdbaf-c2b0-8006-8f99-b4932aca6101

**ArcticMart** sells outdoor gear online and ships within the EU. They are growing fast but still operate with a small IT team. As the company is growing they are revamping the storefront. In this process a threat model has been requested by company leadership to protect the investment
into the new storefront. 

### What are we working on?
The key assets are the database containing customer data including personal and financial information, as well as the actual physical stock that the company holds to sell to their customers.
The storefront gives access to potential customers to the contents of the database of physical stock to see if the items they want are available.
This access needs to be clear and provide a variety of information on the physical stock so the customer can make purchases easily

### What can go wrong?
The main identified risks according to STRIDE: Spoofing, Tampering, Information Disclosure and Denial of Service
Spoofing attacks could be used to use a legitimate users credentials to make purchases in their name
Tampering attacks could be used to change the price or the ammount of an item
Information disclosure attacks could be used to extract financial or personal information, like addresses and credit cards, from the database
Denial of Service attacks could be used to make the storefront unavailable to extort money from the company

The highest risks are Spoofing attacks and Information disclosure as they have the highest impact on customer trust after a possible incident. These are also generally very common techniques used against e-commerce platforms
The lowest risk comes from Denial of Service attacks. While relativly easy to achieve they can as easily be protected against by using third party protections like Cloudflare and the outcome for an attacker is less than certain

### What can we do about it? 

As mentioned above the risk of Denial of Service attacks can not be fully eliminated but it can be mitigated by using third party solutions that protect the traffic to your website
The risk of spoofing attacks could be transferred to a thrid party provider as well by using authentication services like Google, Microsoft or Meta accounts
Access to the database storing customer data needs to have high security standards applied and access should be only given to personel that absolutely need it. 
Databases should be protected against tampering by protecting against common injection techniques and giving elevated access on a need base only
When accessing a database and changing data in it a business justifaction should be required at all times to be able to audit each access to it.

### Did we do a good enough job?

Probably not as the viewpoint taken is by a single individual instead of all stakeholders. On top of that an outside view might be required to be able to also keep internal threats in mind. This threat model was also requested by leadership as a one time exercise so leadership
would need to be educated on the need for continuos threat modeling to stay as informed as possible on the current situation within the system. 







