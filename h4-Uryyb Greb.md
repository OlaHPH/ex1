## h4 Uryyb Greb

<details><summary>Click to open x) Read and summarize - completed 
€ Schneier 2015: Applied Cryptography: 10. Using Algorigthms: 10.1, 10.2, 10.3, 10.4 (from start until the start of "Dereferencing Keys" in 10.4)</summary>
<p>
        
The security of the whole system (data, communication, information, etc. security) is as strong as the weakest link, therefore every element (algorithm, protocol, key management, etc) has to be secure. 

Cryptography is only a very small part of the system - the mathematics of making the system secure. People sometimes focus only on its length while neglect the other aspects. Example: it's much easier to steal data from so's computer by breaking and installing a camera recording computer screen than cryptanalze the hard drive. 

Additionally, the "spy versus spy" cryptography technology is so obsolete as over 99% used in daily operations (bank cards, pay-TV, office building, computer access token, prepayment electricity meter, etc.). In these applications, cryptography role is minor. NSA (National Security Agency) admitted that most securities failures are not because of algorithms or protocol failures, but mainly due to other implementation failures (personel with harmful intention, faulty implementation, integration blunders, etc.) 
                    
#### 10.1 Choosing an algorithm

Available options, all listed below have some issues, 
* published algorithm (ground: as it's out there and already tested by the crytographer and survived) - most sensible option 
* manufacturer (ground: they get to protect their reputation)
* private consultant (ground: they know things)
* the government (ground: the gov protects its citizen interest)
* using their own algorithms (ground: the best, and self trust) 

The algorithms in this book are public and listed with results, both positive and negative with exception of military cryptanalysis - no access. 
 
Algorithms for Export 
* must be approved by the US gov (or actually the NSA - National Security Agency). NSA gets a copy of the source code, but the algorithm's details stay in secret. 
* Non-official practices: 
  * leak a key bit once in a while, embedded in the ciphertext
  * fit the effective key within 30 bit range, example: while the algorithm may accept a 100-bit key, most of those keys might be equivalent (???) 
  * use a fix IV, or encrypt a fixed header at the beginning of each encrypted msg (known-plaintext attack)
  * generate few random bytes, encrypt them with the key, put both the plaintext and ciphertext of those random bytes at the beginning of the encrypted message (known-plaintext attack). 
           
#### 10.2 Public-key cryptography versus symmetric cryptography
        
 Note: terms briefly explained in 1 Foudations, 1.1 Terminology (see Note to self below) 
 
 Both have their own strength and weakness - they are different and solve different problems. 
 Symmetric cryptogaphy is best for encrypting data while public-key outshines in key management and protocols.   
        
#### 10.3 Encrypting communication channels  
 
 OSI models (Open Systems Inconnection) consists of 7 layers - 1. physical, 2. data link, 3. network, 4. transport, 5. session, 6. presentation, 7. application according to [Imperva OSI Model](https://www.imperva.com/learn/application-security/osi-model/)
 * Link-to-link encryption (lowest layers - 1. physical and 2. data link) - 
  * plus - the easiest place to add encryption (generally standardized, easy to connect hadware encryption devices), effective encryption (traffic-flow security - hacker cannot get access to the information, where and how much information is being transferred). Security does NOT depend on any traffic management techniques. Key management is also simple, only 2 endpoints of the line need A COMMON key, and they can change their key independently from the rest of the network, encryption is online
  * minus - EACH physical link in the network needs to be encrypted, leaving any link unencrypted would affect the security of the entire network. Additionally, every node in the network must be protected, since it processes unencrypted data.  
        
 * End-to-end encryption (3. network and 4. transport layers) - encryption device must understand the data according to the protocols up to layer 3. network and encrypt only the transport data units, which are then recombined with the unencrypted routing information and sent to lower layers for transmission (???)
  * plus - avoid encryption/ decryption problem at the physical layer (link-to-link encryption), data remains encrypted until it reaches the final destination.    
  * minus -  prone to traffic analysis (routing information for the data is not encrypted, hacker can learn who communicate to whom, what time, how long WIHOUT knowing contents of these converstaions). Key management is more difficult as individual users must be sure they have common keys, encryption is offline. 

Combining the two -  most expensive but most effective way of securing a network. link-to-link encrypion assure traffic-flow-security, and end-to-end reduces the threat of unencrypted data at the various nodes in the network. Key management for the two schemes can be completely separate: at the physical level (link-to-link) by the network manager and users (end-to-end) encryption. 
        
#### 10.4 Encrypting data for storage (???) - this part is much more challenging to go through comparing to previous 3 

Example: A sends herself a message *in the future* - different problem opened. 
        
In communication channels, messages in transit have no intrinsic (real) value. If A sends B a message, and B doesn't receive the message, A can resend it. NOT for data encrypted for storage. Getting back to the example, A sends her future self a message in the future, and cannot decrypt her own message, she cannot go back in time and decrypt it - it is lost. 

The encryption key has the same value as the message, only smaller. Cryptography breaks large secres into smaller pieces which can be easily lost. Key management procedures: same keys will be used many times, and data may stay on a disk for a while before being decrypted. Note that communication link keys ideally should exist only for the length of communication. For data storage keys, that can be for years, so the keys have to be stored securely for years.

Other issues: 
 * multiple forms of data exists in different locations -> more prone to known-plaintext attack (see brief explanation in 1 Foudations, 1.1 Terminology - as in Note to self below)
 * for DB app, pieces of data may be smaller than the block size of most algorithms ->  encrypted data is bigger than the original. 
 * speed of I/O devices asks for fast EnC/DeC, and may require encryption hardware, or special algorithm 
 * safe, long-term storage for keys required
 * key management is muc more complicated for different users with different privileges
        
Retrieval for encrypted non-structured text files is easier, while for database is much problematic (decrypt the whole DB to access a single record inefficient vs encrypt records independently proning to block-replay attack). On top of that, unencrypted file(s) must be erased after encryption.  
     
Dereferencing keys: 
2 options to encrypt a large hard drive:
 1. Encrypt all the data using a single key -> security issue: large amount of encrypted message can be exposed to hacker, multiple users can see all the files on the drive. 
 2. Encrypt each file with a different key -> issue: usershave to remember different keys for different files.
        
Solution: encrypt each file with a separate key, then encrypt the keys for these file with another key - each user has to remember only one key. Different users can have different subsets of file-encryption keys encrypted with their key, then even master key - more secure option - every file-encryption key is encrypted. (prevent dictionary attack). 
        
Driver-level vs File-level Encryption 
2 ways to encrypt a hard drive:
 1. File-level: every file is encrypted separately. User has to decrypt the file, us, and re-encrypt the file. 
 2. Driver-level: a logical driver on user's machine with all data encrypted, much secure and complex than a simple file-encryption program as its scope is much bigger. The driver would ask user for a password before starting up. This is used to generate the master decryption key used to decrypt actual decryption keys used on different data. 

Providing Random Access to an Encrypted Drive (???) 
Expected feature. Available solutions: 
 1. Use the sectore address to generate a unique IV (Initialization Vector which is random data encrypted as the first block - see 9.3 and CBC - Cipher block chaining mode) for each sector being Enc/Dec. Issue: each sector will ALWAYS be encrypted with the same IV. 
 2. For the master key, generate a pseudo-random block as large as one sector by runing an algorithm in OFB (???) mode. To encrypt any sector, first XOR in this pseudo-random block, than encrypt normally with a block cipher in ECB mode - ECB + OFB. 

As CBC (Cipher Block Chain) and CFB (Cipher Feedback - ???) are error-recovering modes, all the block, except the 1st/ 1st + 2nd block in the sector can be used to generate the IV for that sector. 
Example:
 * IV for sector 3001 can be the hash of all, except fro the first 128 bit of the sector's data.
 * After generating the IV, the sector can be encrypted in CBC mode. 
 * To decrypt, first use the second 64-bit lock of the sector as an IV to decryp the remainder of the sector
 * Then, using the decrypted data, regenerate the IV and decrypt the first 128 bits. (???) 
       
#### Note to self: 
Although not required, I find reading chapter 1  Foundations, 1.1 Terminology provides a general overview and understanding of the most often used terminology in this book. From those: 
 * plaintext (cleartext) - original message (M)
 * encryption - the practice/act/process of disguise the msg to hide its subtance (E) vs decryption (D)
 * ciphertext - encrypted message (C)
 * cryptanalysis - art and science of breaking encrypted (ciphertext) message
 * cipher (cryptographic algorithm) - mathematical function used for encryption (E) and decryption (D) 
 * cryptosytem = algorithm + plaintexts (M) + ciphertexts (C) + keys (K) 
 * symmetric algorithm (conventional algorithm) - encryption key can be calculated from decryption key and vice versa. Usually, encryption key = decryption key (aka. secret-key algorithm, single-key algorithm, or one-key algorithm). Sender and receiver have to agree on a key BEFORE they can communicate securely. So, the key must remain secret in order to keep the communication secret. SA can be divided into stream algorithm and block algorithm. 
 * public-key algorithm (asymetric algorithm) - encryption key (public key) <> decryption key (private key), and decryption key CANNOT be calculated from encryption key which can be made public.
 * ciphertext-only attack - the hacker has access to several ciphertexts (encrypted messages) with the same encryption algorithm, he tries to recover as many plaintexts as possible, or even try to find out the encryption key to decrypt other ciphertexts with the same keys. 
 * known-plaintext attack - the hacker has access to several plaintext messages and their corresponding ciphertexts, he tries to find out the encryption key/algorithm to decrypt any NEW ciphertexts encrypted with the same keys. 
 * chosen-plaintext attack 
 * adaptive-chosen plaintext attack  
 * chosen-ciphertext attack
 * block-replay attack (???) 
</p>
</details>
<details><summary>Click to open y) Choose a password manager - completed </summary>
<p>
The password manager I chose here is 1Password. In general, password managers are apps which generate strong passwords, securely store them and automatically fill them in on websites/apps where login is required. Apart from passwords, 1Pass stores and manages other sensitive information such as credit card numbers, secure notes and personal identities.  1Pass is built based on the open-source SQLite database format and uses algorithms that expers have examined and verified to keep information safe. 

* What threats does it protect against? In general, sensitive data exposure (login details, password, credit card numbers, bank account details, secure note, etc), data breach. In particular, 1Password protects users from password reuse, brute-force attack (hacker trying to guess the password by trying every possible characters combination systematically), phishing attacks, keyloggers and physical thefts. 
        
* What information is encrypted, what's not? 
     
 * data like passwords, personal information - credit card info, bank account, passport details, secure notes are encrypted,  (credentials 8account password,  secret key) are never sent over the network
 * data not encrypted are either required to operate 1Password itself (name of password vaults, URL of websites where the passwords are saved to, register email address, metadata related to account activity - account creation date, and modification date) or data considered not sensitive. 
    
* What's the license? How would you describe license's effects or categorize it?
 different licences are available, among them: 
  * subcription license - most common model (monthly/annually fee)  
  * individual license - one time payment for a single user 
  * family license - one time payment license for up to 5 family members on multiple devices    
  * business licence - subscription-based with extra features and supports.     
        
* Where is the data stored? If in "the cloud", which country / juristiction / which companies? If on local disk, where?
        
Location of users' data storage depends on the version and users' preferences, availabe options are:
 1. Local storage - for standalone version user (individual license) at user's computer hard drive or mobile device's internal storage.  
 2. Cloud storage - for subcription license users 
 3. Local network storage - extra option for business licence user

1Password is subject to Canadian laws and regulations as they are based in Canada, however, depending on the storage location, extra regional legal compliance may apply. 
        
* How is the data protected? 
        * end-to-end encryption model using AES-GCM-256 authenticated encryption (??? explaination needed), 
        * PBKDF2-HMAC-SHA256 for key derivation, account password is NOT stored alongside the 1Password data or transmitted over the network
 * the data in user's 1Password account is protected by the 128-bit Secret Key which is combined with the user's account password to encrypt the data. 

Other features: 
 * clipboard management - can be set to remove passwords from user's clipboard automatically 
 * code signature validation - 1Password examines the browsers' reliabilities before letting user enter sensitive information
 * auto-lock - AFK or when closing the laptop 
 * watchover vulnerability alerts  - sending warning once a website has been hacked
 * phishing protection - filling in passwords on the sites where they are saved 
 * 1Password displays or fills data only when requested by the user
 * biometric accesss option available (fingerprint)
 * secure remote password (SRP)    
  </p>
  </details>
<details><summary>Click to open a) Demonstrate the use of a password manager - completed </summary>
  <p>
Using 1Password is simple and straightforward, below how I created a free account and set up my password for the 1Password account and store password to a site (hhmoodle.haaga-helia.fi). 

1Password setup instruction can be found at [Set up 1Password](https://support.1password.com/explore/get-started/?utm_source=google&utm_medium=cpc&utm_campaign=18322456510&utm_content=&utm_term=&gclid=Cj0KCQiA6fafBhC1ARIsAIJjL8n2dNt3MSlp5vouoOxoVbbjBInVue4Bv_Tu0uttJPF8YF9aDrFfWCQaAm-0EALw_wcB&gclsrc=aw.ds)          
          
<img width="487" alt="1password-demo-01" src="https://user-images.githubusercontent.com/99587532/221982737-fcbc7f06-2540-4674-addb-ec6fed24dee2.png">
<img width="512" alt="1password-demo-02" src="https://user-images.githubusercontent.com/99587532/221982742-c89921b9-9c1d-46e2-9e36-90d952ffd9c9.png">
<img width="578" alt="1password-demo-03" src="https://user-images.githubusercontent.com/99587532/221982744-54d8f912-019d-435c-916b-c1b4dd763d2f.png">
<img width="353" alt="1password-demo-04" src="https://user-images.githubusercontent.com/99587532/221982746-a35c87d0-658f-4a9e-8b41-cd127ea140b2.png">
<img width="278" alt="1password-demo-05" src="https://user-images.githubusercontent.com/99587532/221982748-9ff62ae9-2c0a-4f70-9fb3-e18d88444b27.png">
<img width="446" alt="1password-demo-06" src="https://user-images.githubusercontent.com/99587532/221982751-45b41a05-d380-4283-aa8f-fadf88c33fca.png">
<img width="617" alt="1password-demo-07" src="https://user-images.githubusercontent.com/99587532/221982752-b59ba445-2c19-4405-b44f-79a2093bd2c7.png">
<img width="617" alt="1password-demo-08" src="https://user-images.githubusercontent.com/99587532/221982753-c2782a53-f332-4fd6-b686-6aebc0cbe19a.png">
<img width="616" alt="1password-demo-09" src="https://user-images.githubusercontent.com/99587532/221982754-99fd7839-bd35-41fb-b6a4-e349b45a1a33.png">
<img width="605" alt="1password-demo-10" src="https://user-images.githubusercontent.com/99587532/221982755-3f17ce8c-ae93-41aa-aad9-a9f1a083fb17.png">
<img width="626" alt="1password-demo-11" src="https://user-images.githubusercontent.com/99587532/221982756-c1559427-2b38-442b-b84c-be965195bcb3.png">
<img width="611" alt="1password-demo-12" src="https://user-images.githubusercontent.com/99587532/221982758-e611c89d-73a9-4df2-ac95-b16f571ea235.png">

  </p>
</details>
<details><summary>b) Encrypt and decrypt a message (you can use any tool you want, gpg is one option)- TBC </summary>
  <p>
  </p>
</details>
<details><summary>c) Voluntary bonus: send and receive encrypted message over email.- TBC </summary>
  <p>
  </p>
</details>
<details><summary> d) Voluntary difficult bonus, requries coding skills: Cryptopals (recommended, if you have what it takes).- TBC </summary>
  <p>
  </p>
</details>
 <details><summary>   e) Voluntary bonus, easy: try rot13, the military grade top-secret encryption of the top-2 empire of year zero. 
  Could double rot13 provide extra security?- TBC </summary>
  <p>
  </p>
</details>

## References 
* [Information Security course taught by Tero Karvinen](https://terokarvinen.com/2023/information-security-2023/)
* [OSI Model](https://www.imperva.com/learn/application-security/osi-model/)
* [Take Control of 1Password, 6th Edition, Joe Kissell](https://learning.oreilly.com/library/view/take-control-of/9781990783180/text/ch005.xhtml#LearnPasswordSecurityBasics)
* [What is a password manager? How it works, and other FAQs](https://blog.1password.com/password-manager/?utm_source=google&utm_medium=cpc&utm_campaign=18322456510&utm_content=&utm_term=&gclid=EAIaIQobChMIuNairOW4_QIVAEeRBR1u2w23EAAYAyAAEgLbBfD_BwE&gclsrc=aw.ds)
* [How do password managers work](https://cybernews.com/best-password-managers/how-do-password-managers-work/)
* [1Password comparison](https://1password.com/comparison/)
* [1Password security](https://support.1password.com/1password-security/)
* [All-time favorite Matthieu's assignment report for inspiration](https://github.com/MatthieuBruh/h5_UryybGreb)
* [Set up 1Password](https://support.1password.com/explore/get-started/?utm_source=google&utm_medium=cpc&utm_campaign=18322456510&utm_content=&utm_term=&gclid=Cj0KCQiA6fafBhC1ARIsAIJjL8n2dNt3MSlp5vouoOxoVbbjBInVue4Bv_Tu0uttJPF8YF9aDrFfWCQaAm-0EALw_wcB&gclsrc=aw.ds)

