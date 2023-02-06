h3 Attaaack
 
<details><summary> x) Read and summarize </summary>
<p> 
        € Costa-Gazcón 2021: Practical Threat Intelligence and Data-Driven Threat Hunting. Chapter 4: Mapping the Adversary 
        (all but "Testing yourself", which is left as voluntary bonus)
 1. The WITRE ATT&CK framework
 
  Description of 14 TTPs (tactics, techniques (+subtechniques), procedures) according to WITRE ATT&CK framwework.
  Each tactic has its own set of techniques/subtechniques with specific TA behaviors. 
   1. Reconnaissance  - new - trying to get as much info about the victim as possible 
   2. Resources Dev - new - conducting assessing resources process (these resources can be purchased, stolen, or developed)
   3. Initial Access - the very first step to get into victim's environment and get a foothold in the network using entry vectors
   4. Execution - using mali code inside victim's environment 
   5. Persistence - trying to stay inside victim' system 
   6. Privilige Escalation - trying to upgragde their access level, privilige, permission
   7. Defense Evation - avoiding to be detected by the victim's defense 
   8. Credential access - taking/ stealing user's credetial access to gain access fruther into the system, or to disguise their malicious activities 
   9. Discovery - gaining knowledge on how victim's environment is built
   10. Lateral movement - discovering how victim's network and system are configured, then pivoting from 1 to another until getting the target 
   11. Collection - collecting info from victim's environment for further exfiltration
   12. Command & Control - communication with the system after control it
   13. Exfiltration - stealing info why trying to stay undetected
   14. Impact - preventing users from accessing the system (manipulating/destroying the system and on)
 
 Procedure is the specific way a TA implements a specific techniques or subtechniques. A procedure can cover multiple techniques and subtechniques as well. 
 
 The ATT&CK Matrix 
 
  Introduction to MITRE ATT&CK Matrix for Enterprise with tactics and theirs specific techniques related with expansion to techniques specifications (ID,     procedure examples, mitigation, detection and on) making ATT&CK a great resource for training, studying, planning and mapping. (Term used here - _"planning blue and red teaming exercises"_ a training strategy where the "red team" is the one trying to attack (TA) and the "blue team" is the one trying to defend. 
Source: [Cloud Range - Red Team vs. Blue Team excercises](https://www.cloudrangecyber.com/red-vs-blue-team)
 
 ![h3_i_Matrix_01](https://user-images.githubusercontent.com/99587532/216986406-dc57c2ef-2c8b-4c91-b3ce-06f2fe0c22af.png)
 
 Source: [Deploy Container](https://attack.mitre.org/versions/v12/techniques/T1610/) 
 
  The ATT&CK Navigator 
 
  Brief introduction to use the ATT&CK navigator which is a great studying tool to visualize a TA ' modus operandi ("a method of procedure"), or generate a security exercise. I found the introduction too brief, and took use of [Comparing layers in ATT&CK Navigator Walkthrough](https://attack.mitre.org/docs/training-cti/Comparing%20Layers%20in%20Navigator.pdf) which provided a much comprehensive instruction. 
 
 2. Mapping with ATT&CK
 
  Example of identifying ATT&CK tactics used in the case of Virus Bulletin 2018: Inside Formbook Infostealer by the malware researcher Gabriela Nicolao: (https://www.virusbulletin.com/uploads/pdf/magazine/2018/VB2018-Nicolao.pdf)
 
 3. Testing yourself 
 </p> 
 </details>   
 <details><summary> y) Write an answer with references.</summary>
 <p> 
  Answer in the context of Mitre Att&ck, and pick examples that are different from the chapter in task x.
   * Define tactic and give an example.

  The one I picked here is Execution (https://attack.mitre.org/tactics/TA0002/). As briefly mentioned in the previous part, execution refers to the act of TA running malicious code inside the victim's environment, either local or remote. This is usually paired with other tactics' techniques to acchieve broader goals, like getting data or "getting to know" the network, system. 
  
   * Define technique and subtechnique, and give an example of each.
  
There are 13 techniques included in this tactic and 21 subtechniques, of those, I focus on 
 T1204. User Execution and its subtechniques (malicious emails, links and/or images). User Execution usually goes in pair with other techniques, among them, most often, Phishing from Initial Access or may also occur at later phases of an instrution, for example, Command and Control via Remote Access Software. Using this tactic, TA "tricks" (social engineers) the victims into conducting specific actions to gain excecution. Few examples: 
  * user executing malicious code by opening a malicious document file, or links - in my opinion, this is one of most common/frequent form of techniques used. The TA (phisher/scammer) would send a "fake" email (looking like a legit one) containing a link asking for action from the user/victim. The user then clicks on the link which triggers downloading some malware and this later exploits. 
  * user opening a file in a shared directory placed by the TA 
  * user enabling Remote Access Software, letting TA have direct control of the system. 
  
   * Define procedure, and give an example of each.
 </p> 
 </details>       
 <details><summary> a) Webgoat: A3 Sensitive data exposure </summary>
 <p> 
        Insecure Login: 2 Let's try
 </p> 
 </details>  
 <details><summary> n) Voluntary bonus:   </summary>
 <p> 
  "Testing yourself" in Costa-Gazcón: Practical Threat Intelligence and Data-Driven Threat Hunting
  Chapter 4: Mapping the Adversary
 The very first techniques I was able to identify was User Execution: Malicious File (ID: T1204.002) and Malicious Link (ID: T1204.001) focusing on _"Formbook […] was distributed via PDFs with embedded links, DOC and XLS files with malicious macros, and compressed files containing the executable"_

 
 </p> 
  </details>  
  <details><summary> m) Voluntary difficult bonus: </summary>
  <p> 
  WebGoat: SQL Injection (advanced).
  </p> 
  </details>  
  
Tips:
    O'Reilly Learning € (former Safari) is a bit pricey, but Haaga-Helia students get free access trough Haaga-Helia library A-Z page.
    
 <details><summary> References </summary>
 <p> 
  *[€ Costa-Gazcón 2021: Practical Threat Intelligence and Data-Driven Threat Hunting Chapter 4: Mapping the Adversary](https://www.oreilly.com/library/view/practical-threat-intelligence/9781838556372/B13376_04_Final_SK_ePub.xhtml#_idParaDest-75)
  * (https://learning.oreilly.com/library/view/practical-threat-intelligence/9781838556372/B13376_04_Final_SK_ePub.xhtml#_idParaDest-71)
  *[MITRE ATT&CK®](https://attack.mitre.org/)
  *[Mitre|ATTC&K - Enterprise Matrix](https://attack.mitre.org/matrices/enterprise/)
  *[Cloud Range - Red Team vs. Blue Team excercises](https://www.cloudrangecyber.com/red-vs-blue-team)
  *[Mitre ATT&CK Navigator](https://mitre-attack.github.io/attack-navigator/)
  *[Comparing layers in ATT&CK Navigator Walkthrough](https://attack.mitre.org/docs/training-cti/Comparing%20Layers%20in%20Navigator.pdf)
  *[Virus Bulletin 2018: Inside Formbook Infostealer](https://www.virusbulletin.com/uploads/pdf/magazine/2018/VB2018-Nicolao.pdf)
  *[Matthieu's assignment report for the y part](https://github.com/MatthieuBruh/h3_Attaaack)
  *[Mitre|ATT&CK-Execution](https://attack.mitre.org/tactics/TA0002/)
  *[CVE to T&TS: Using CVE attributes for MITRE ATT&CK mapping](https://l.vulcancyber.com/hubfs/Ebooks-and-White-Papers/Vulcan-Cyber-Mapping-CVEs-to-MITRE.pdf)
  *[Wikipedia-Social Engineering(security)](https://en.wikipedia.org/wiki/Social_engineering_(security))
 </p> 
 </details>  
