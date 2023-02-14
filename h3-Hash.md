# h3 Hash

<details><summary>Click herex) Read and summarize - completed</summary>
<p>
(This subtask x does not require tests with a computer. Some bullets per article is enough for your summary, feel free to write more if you like)
€ Schneier 2015: Applied Cryptography: 2.3 One-Way Functions and 2.4 One-Way Hash Functions.
 
2.3 One-Way Functions
* OWF is the central conception of public-key cryptography
* OWF is not a protocol itself but serves as a fundamental building block of most of protocols discussed in the book.
* OWF is easy to build, but remarkably much complicated to reverse
* Example: to break a plate into thousand pieces is easy, but to put these thousands pieces back into the plate is comparatively super hard. 
* The great thing about OWF - we can NOT use OWF for public-key encryption as is because people cannot decrypt it (still the plate but containing a message, break it into thousands pieces, then ask a friend to put the pieces into a plate and READ the msg - NOPE).
* A trapdoor OWF - a special type of OWF with a secret trapdoor (secret information, instruction)
* Example: it's easy to dismantle a watch into pieces, and it's super hard to put these pieces back together into a watch, but it would be doable with an instruction. 

2.4 One-Way Hash Functions
* OWHF has many names - compression function, contraction function, msg digest, fingerprint, cryptographic checksum, msg integrity check (MIC), manipulation detection code. 
* OWHF is central to modern cryptography
* HF has been used in Computer Science for a long time.
* HF is a mathematical function where you convert a variable-length input string (pre-image) into fixed-length output string (hash value). 
* HF is many-to-one, we cannot use them to determine 2 strings are equal, but can use them to get a reasonable assumption of accuracy. 
* OWFH works in one way so pre-image -> hash value, NOT hash value -> pre-image, OWFH is collision-free 
* Example: HF with public key is used usually in financial transactions, asking someone to provide the correct hash value to release an amount of money from account 
* MAC (message authentication code) or DAC (data authentication code) = OWHF + secret key with hash value  = f(preimage, key) 
* with MAC/DAC - only someone with the KEY can verify the hash value
     
My thought: The chapter is a great introduction to cryptography. The language used is very down-to-earth, and fun to read. 
</p> 
 </details>  
<details><summary>a) Install Hashcat. See Karvinen 2022: Cracking Passwords with Hashcat-TBC</summary>
    <p>
I got stuck with this task, and got to Matthieu's report for inspiration (cannot recommend his enough) but even Matthieu's couldn't help me get through this task this time.

So I successfully installed hashcat, created a new director "hashed" as instructed in Tero's guide.
At the next step, I got the "Rockyou" dictionary downloaded and used command wc -l (word count, and here number of lines) in the file rockyou. 
     
I also got to identify the type of the hash using command -m 


    </p> 
 </details> 
<details><summary>b) Crack this hash: 8eb8e307a6d649bc7fb51443a06a216f-TBC</summary>
    <p>
    </p> 
 </details> 
<details><summary>c) Compile John the Ripper, Jumbo version. Karvinen 2023: Crack File Password With John.-TBC</summary>
    <p>
    </p> 
 </details> 
<details><summary>d) Crack a zip file password-TBC</summary>
    <p>
    </p> 
 </details> 
<details><summary>n) Voluntary: create a password protected file other than ZIP. Crack the password. How many formats can you handle?-TBC</summary>
    <p>
    </p> 
 </details>
 
 ### References 
 * [Tero Karvinen-h3 Hash assignment](https://terokarvinen.com/2023/information-security-2023/?f=moodle)
 * [€ Schneier 2015: Applied Cryptography: 2.3 One-Way Functions and 2.4 One-Way Hash Functions](https://www.oreilly.com/library/view/applied-cryptography-protocols/9781119096726/10_chap02.html#chap02-sec003)
 * [Karvinen 2022: Cracking Passwords with Hashcat](https://terokarvinen.com/2022/cracking-passwords-with-hashcat/)
 * [Karvinen 2023: Crack File Password With John](https://terokarvinen.com/2023/crack-file-password-with-john/)
 * [Matthieu's assignment report](https://github.com/MatthieuBruh/h4_Hash) Again, it's done so well, it's such a pleasure to read. For anyone needing an inspiration, or just in vain like me, check Matthieu, please
