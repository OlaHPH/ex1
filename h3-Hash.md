# h3 Hash

<details><summary>x) Read and summarize - TBC</summary>
<p>
(This subtask x does not require tests with a computer. Some bullets per article is enough for your summary, feel free to write more if you like)
€ Schneier 2015: Applied Cryptography: 2.3 One-Way Functions and 2.4 One-Way Hash Functions.
</p>
    <p> 2.3 One-Way Functions 
* OWF is the central conception of public-key cryptography
* OWF is not a protocol itself but serves as a fundamental building block of most of protocols discussed in the book.
* OWF is easy to build, but remarkably much complicated to reverse
* Example: it's easy to break a plate into thousand pieces, but it's super hard to put these thousands pieces back into the plate. 
* The great thing about OWF - we canNOT use OWF for public-key encryption as is because people cannot decrypt it (still the plate but containing a message, break it into thousands pieces, then ask a friend to put the pieces into a plate and READ the msg - NOPE).
* A trapdoor OWF - a special type of OWF with a secret trapdoor (secret information, instruction)
* Example: it's easy to dismantle a watch into pieces, and it's super hard to put these pieces back together into a watch, but it would be doable with an instruction. 

        ## 2.4 One-Way Hash Functions
        *OWHF has many names - compression function, contraction function, msg digest, fingerprint, cryptographic checksum, msg integrity check (MIC), manipulation detection code. 
        * OWHF  is central to modern cryptography
        * HF has been used in Computer Science for a long time.
        * HF is a mathematical function where you convert a variable-length input string (pre-image) into fixed-length output string (hash value). 
        * HF is many-to-one (??? - further explanation needed), we cannot use them to determine 2 strings are equal, but can use them to get a reasonable assumption of accuracy. 
        * OWFH works in one way so pre-image -> hash value, NOT hash value -> pre-image, OWFH is collision-free (??? further explanation needed)
        * Example: in financial transactions, asking so to provide the correct hash value to release an amount of money from account 
        * MAC (message authentication code) or DAC (data authentication code) = OWHF + secret key with hash value  = f(preimage, key) 
        * with MAC/DAC - only someone with the KEY can verify the hash value
     
     The chapter is a great introduction to cryptography. The language used is very down-to-earth, and fun to read. I read through the 2.1 and 2.2 although it's not requested. 
    </p>
</p> 
 </details>  
<details><summary>a) Install Hashcat. See Karvinen 2022: Cracking Passwords with Hashcat-TBC</summary>
    <p>
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
