<ol>
    <li>
        <a target="_blank" href="https://tryhackme.com/room/cryptographybasics"><h1>Cryptography Basics</h1></a>
        <ul>
            <li><h2>Importance Of Cryptography:</h2><p>Cryptography's purpose is to ensure secure communication win the presence of adversaries, the term "secure" includes the confidentiality and integrity of the communicated data and the authenticity of the parts communicating.</p>
            <div><h4>Task:</h4> What is the standard required for handling credit card information? Answer: PCI DSS</div>
            </li>
            <li><h2>Plaintext To Ciphertext:</h2>
                <ul>
                    <li>Plaintext: the original readable data before encryption.</li>
                    <li>Ciphertext: the scrambled unreadable message after encryption.</li>
                    <li>Cipher: the algorithm or method that turns plaintext to ciphertext and back again.</li>
                    <li>Key: a string of bits the Cipher uses to encypt or decrypt data.</li>
                </ul>
            </li>
            <div><h4>Tasks:</h4>
            What do you call the encrypted plaintext? Ciphertext.
            <br>What do you call the process that returns the plaintext?: Decryption.</div>
            <li><h2>Types Of Encryption:</h2>
                <h3>Symmetric Encryption:</h3><p>Is the type of encryption that uses the same key for encryption and decryption, communicating the key to the intended parties can be challenging. Examples of Symmetric encryption are DES(Data Encryption Standard), 3DES(Triple DES), and AES(Advanced DS)</p>
                <h3>Asymmetric Encryption:</h3><p>Uses a public key for encryption and a private key for decryption. Examples: RSA, Diffie Hellman, and ECC(Eleptic Curve Cryptography)</p>
                <div><h4>Tasks:</h4>
                Should you trust DES? (Yea/Nay). Answer: Nay.
                <br>When was AES adopted as an encryption standard? Answer: 2001.</div>
            </li>
            <li><h2>Basic Math:</h2><p>The building blocks of modern cryptography lie in mathematics. The next two mathematical operations are used in multiple algorithms:</p>
                <h3>XOR(Exclusive OR) Operation:</h3><p>In binary, XOR compares two bits and returns 1 if the bits are different and 0 if they are the same.</p>
                <h3>Modulo Operation</h3><p>Commonly written as % or as mod. The modulo operator, X%Y, is the remainder when X is divided by Y.</p>
                <div><h4>Tasks:</h4>
                What’s 1001 ⊕ 1010? Answer: 0011
                <br>What’s 118613842%9091? Answer: 3565
                <br>What’s 60%12? Answer: 0</div>
            </li>
        </ul>
    </li>
    <br>
    <li>
        <a target="_blank" href="https://tryhackme.com/room/publickeycrypto"><h1>Public Key Cryptography Basics</h1></a>
            <ul>
                <li>
                    <h2>Common Use Of Asymmetric Encryption:</h2><p>One of the most common use cases of asymmetric cryptography is exchanging keys for symmetric encryption. Asymmetric encryption is relatively slow compared to symmetric encryption; therefore we rely on it to negotiate and agree on symmetric encryption cipher and keys.</p>
                    </li>
                    <li><h2>RSA:</h2><p>Is a public key encryption algorithm that enables secure data transmission over insecure channels. The math behind RSA comes up relatively often in CTFs.</p>
                    <h3>The Math That Makes RSA Secure:</h3>
                    <ol>
                        <li>Bob chooses two prime numbers: <span ><em>p</em> = 157</span> and <span ><em>q</em> = 199</span>. He calculates <span ><em>n</em> = <em>p</em> × <em>q</em> = 31243</span>.
                        </li>
                        <li>With <span ><em>ϕ</em>(<em>n</em>) = <em>n</em> − <em>p</em> − <em>q</em> + 1 = 31243 − 157 − 199 + 1 = 30888</span>, Bob selects <span ><em>e</em> = 163</span> such that <span ><em>e</em></span> is relatively prime to <span ><em>ϕ</em>(<em>n</em>)</span>; moreover, he selects <span ><em>d</em> = 379</span>, where <span ><em>e</em> × <em>d</em> = 1</span> mod <span ><em>ϕ</em>(<em>n</em>)</span>, i.e., <span ><em>e</em> × <em>d</em> = 163 × 379 = 61777</span> and <span >61777</span> mod <span >30888 = 1</span>. The public key is <span >(<em>n</em>,<em>e</em>)</span>, i.e., <span >(31243,163)</span> and the private key is $(n,d), i.e., <span >(31243,379)</span>.</li>
                        <li>Let’s say that the value they want to encrypt is <span ><em>x</em> = 13</span>, then Alice would calculate and send <span ><em>y</em> = <em>x</em><sup><em>e</em></sup></span> mod <span ><em>n</em> = 13<sup>163</sup></span> mod <span >31243 = 16341</span>.</li>
                        <li>Bob will decrypt the received value by calculating <span ><em>x</em> = <em>y</em><sup><em>d</em></sup></span> mod <span ><em>n</em> = 16341<sup>379</sup></span> mod <span >31243 = 13</span>. This way, Bob recovers the value that Alice sent.</li>
                    </ol>
                    <div><h4>Tasks:</h4>
                    Knowing that p = 4391 and q = 6659. What is n? Answer: 29239669
                    <br>Knowing that p = 4391 and q = 6659. What is ϕ(n)? Answer: 29228620</div>
                </li>
                <li>
                    <h2>Diffie Hellman Key Exchange:</h2><p>Is often used alongside RSA, DH is used for key agreement, while RSA is used for digital signatures,key transport, authintication..etc.</p>
                    <h3>The Math Behind Deffie Hellman:</h3>
                    <ul>
                        <li>Alice and Bob agree on the public variables: a large prime number p and a generator g, where 0 < g < p. These values will be disclosed publicly over the communication channel. Although insecurely small, we will choose p = 29 and g = 3 to simplify our calculations.</li>
                        <li>Each party chooses a private integer. As a numerical example, Alice chooses a = 13, and Bob chooses b = 15. Each of these values represents a private key and must not be disclosed.</li>
                        <li>It is time for each party to calculate their public key using their private key from step 2 and the agreed-upon public variables from step 1. Alice calculates A = ga mod p = 313 mod 29 = 19 and Bob calculates B = gb mod p = 315 mod 29 = 26. These are the public keys.</li>
                        <li>Alice and Bob send the keys to each other. Bob receives A = ga mod p = 19, i.e., Alice’s public key. And Alice receives B = gb mod p = 26, i.e., Bob’s public key. This step is called the key exchange.</li>
                        <li>Alice and Bob can finally calculate the shared secret using the received public key and their own private key. Alice calculates Ba mod p = 2613 mod 29 = 10 and Bob calculates Ab mod p = 1915 mod 29 = 10. Both calculations yield the same result, gab mod p = 10, the shared secret key.</li>
                    </ul>
                    <div><h4>Tasks:</h4>
                    Consider p = 29, g = 5, a = 12. What is A? Answer: 7
                    <br>Consider p = 29, g = 5, b = 17. What is B? Answer: 9
                    <br>Knowing that p = 29, a = 12, and you have B from the second question, what is the key calculated by Bob? (key = Ba mod p). Answer: 24
                    <br>Knowing that p = 29, b = 17, and you have A from the first question, what is the key calculated by Alice? (key = Ab mod p). Answer: 24</div>
                </li>
                <li>
                    <h2>SSH:</h2><p>SSH uses private keys to authenticate servers and private keys to authenticate the client.</p>
                    <div><h4>Tasks:</h4>
                    Check the SSH Private Key in ~/Public-Crypto-Basics/Task-5. What algorithm does the key use? Answer: RSA</div>
                </li>
                 <li>
                    <h2>Digital Signatures and Certificates:</h2>
                    <h3>Digital Signatures:</h3><p>provide a way to verify the authenticiy and integrity of a digital message or document using asymmetric cryptography.</p>
                    <h3>Certificates:</h3><p>are an essential application of public key cryptography. A common place for their use is HTTPS; how does the browser know that the server is the real one.</p>
                    <div><h4>Tasks:</h4>
                    What does a remote web server use to prove itself to the client? Answer: Certificate
                    <br>What would you use to get a free TLS certificate for your website? Answer: Let's Encrypt</div>
                </li>
                <li>
                    <h2>PGP And GPG:</h2><p>PGP stand for Pretty Good Privacy, it's a software that implements encryption for files. GPG is an open-source implenetation of the PGP standard.</p>
                    <div><h4>Tasks:</h4>
                    Use GPG to decrypt the message in ~/Public-Crypto-Basics/Task-7. What secret word does the message hold? Answer: Pineapple</div>
                </li>
            </ul>
    </li>
    <br>
    <li>
        <a target="_blank" href="https://tryhackme.com/room/hashingbasics"><h1>Hashing Basics:</h1></a>
        <ul>
            <li><h2>Hash Functions:</h2>
                <p>Hash functions are different from encryption, there is no keys, and it's meant to be impossible to go from output back to input. A hash function takes some input data of any size and creates a summary of that data, the output has a fixed size.</p>
                <div><h4>Tasks:</h4>
                    What is the SHA256 hash of the passport.jpg file in ~/Hashing-Basics/Task-2? Answer: 77148c6f605a8df855f2b764bcc3be749d7db814f5f79134d2aa539a64b61f02
                    <br>What is the output size in bytes of the MD5 hash function? Answer: 16
                    <br>If you have an 8-bit hash output, how many possible hash values are there? Answer: 256</div>
            </li>
            <li><h2>Insecure Password Storage For Authentication And Using Hashing For Secure Storage:</h2>
                <p>Storing passwords in plaintext is insecure, this is where hashing come in, instead of storing passwords as plaintext we store their hashes, so that even if the stored list gets leaked, the hacker will have to crack each password.</p>
                <p>Drawback: what if two users have the same password? they'll have the same hash, It also means someone can create a Rainbow Table to break the hashes. A Rainbow Table is a lookup table of hashes to plaintexts, so you can quickly find out what password a user had just from the hash.</p>
                <p>To protect from rainbow tables we use salt. Salt is a randomly generated value stored in the database ans should be unique to each user, it's added to the start or the end of the password before it's hashed. This means every user will have a unique hash even if another user have the same password.</p>
                <div><h4>Tasks:</h4>
                What is the 20th password in rockyou.txt? Answer: qwerty
                <br>Manually check the hash “4c5923b6a6fac7b7355f53bfe2b8f8c1” using the rainbow table above. Answer: inS3CyourP4$$
                Crack the hash “5b31f93c09ad1d065c0491b764d04933” using an online tool. Answer: tryhackme
                <br>Should you encrypt passwords in password-verification systems? Yea/Nay. Answer: Nay</div>
            </li>
            <li><h2>Recognizing Password Hashes:</h2>
                <p>On UNIX/LINUX systems; the shadow file contains the password info, each line contains nine fields, seperated by a colons(:), the first two fields are the login name and the encrypted password, the password field is saved in the format <code>$prefix$options$salt$hash</code> </P>
                <p>MS Windows passwords are hashed using NTLM, a variant of MD4. They’re visually identical to MD4 and MD5 hashes, so it’s very important to use context to determine the hash type.On MS Windows, password hashes are stored in the SAM (Security Accounts Manager).</p>
            </li>
            <div><h4>Tasks:</h4>
                    What is the hash size in yescrypt? Answer: 256
                    <br>What’s the Hash-Mode listed for Cisco-ASA MD5? Answer: 2410
                    <br>What hashing algorithm is used in Cisco-IOS if it starts with $9$? Answer: scrypt</div>
            <li><h2>Password Cracking:</h2>
                <p>Went through cracking hashes using hashcat. Syntax: <code>hashcat -m hash_type -a attack_mode hashfile wordlist</code>where:</p>
                <ul>
                    <li><code>-m hash_type</code> specifies the hash-type in numeric format. For example, <code>-m 1000</code> is for NTLM. Check the official documentation (man hashcat) and example page to find the hash type code to use.</li>
                    <li><code>-a attack_mode</code> specifies the attack-mode. For example, <code>-a 0</code> is for straight, i.e., trying one password from the wordlist after the other.</li>
                    <li><code>hashfile</code> is the file containing the hash you want to crack.</li>
                    <li><code>wordlist</code> is the security word list you want to use in your attack.</li>
                </ul>
                <p>Example: <code>hashcat -m 3200 -a 0 hash.txt /usr/share/wordlists/rockyou.txt</code></p>
                <div><h4>Tasks:</h4>
                    Use hashcat to crack the hash, $2a$06$7yoU3Ng8dHTXphAg913cyO6Bjs3K5lBnwq5FJyA6d01pMSrddr1ZG, saved in ~/Hashing-Basics/Task-6/hash1.txt. Answer: 85208520
                    <br>Use hashcat to crack the SHA2-256 hash, 9eb7ee7f551d2f0ac684981bd1f1e2fa4a37590199636753efe614d4db30e8e1, saved in saved in ~/Hashing-Basics/Task-6/hash2.txt. Answer: halloween
                    <br>Use hashcat to crack the hash, $6$GQXVvW4EuM$ehD6jWiMsfNorxy5SINsgdlxmAEl3.yif0/c3NqzGLa0P.S7KRDYjycw5bnYkF5ZtB8wQy8KnskuWQS3Yr1wQ0, saved in ~/Hashing-Basics/Task-6/hash3.txt. Answer: spaceman
                    <br>Crack the hash, b6b0d451bbf6fed658659a9e7e5598fe, saved in ~/Hashing-Basics/Task-6/hash4.txt. Answer: funforyou</div>
            </li>
            <li><h2>Hashing For Integrity Checking:</h2>
                <p>Hashing can be used to check that files haven't been changed, if you put the same data in, you'll get the same data out.</p>
                <div><h4>Tasks:</h4>
                    What is SHA256 hash of libgcrypt-1.11.0.tar.bz2 found in ~/Hashing-Basics/Task-7? Answer: 09120c9867ce7f2081d6aaa1775386b98c2f2f246135761aae47d81f58685b9c
                    <br>What’s the hashcat mode number for HMAC-SHA512 (key = $pass)? Answer: 1750</div>
            </li>
        </ul>
    </li>
    <br>
    <li>
        <a target="_blank" href="https://tryhackme.com/room/johntheripperbasics"><h1>John the Ripper: The Basics</h1></a>
        <p>John The Ripper is a well known hash cracking tool for conducting fast brute force attacks over various hash types</p>
        <ul>
            <li><h2>Cracking Basic Hashes:</h2>
                <p><h4>Basic Syntax:</h4> <code>john [options] [file path]</code></p>
                <p><h4>Automatic Detecting:</h4>John has built-in features to detect what type of hash it’s being given and to select appropriate rules and formats to crack it for you; this isn’t always the best idea as it can be unreliable, but if you can’t identify what hash type you’re working with and want to try cracking it, it can be a good option! To do this, we use the following syntax: </p>
                <code>john --wordlist=[path to wordlist] [path to file]</code>
                <p><h4>Identifying Hashes:</h4>Sometimes, John won’t play nicely with automatically recognising and loading hashes, but that’s okay! We can use other tools to identify the hash and then set John to a specific format. There are multiple tools online for hash identifying like: <a target="_blank" href="https://hashes.com/en/tools/hash_identifier">hashes.com</a> and <a target="_blank" href="https://gitlab.com/kalilinux/packages/hash-identifier/-/tree/kali/master">Hash Identifier</a>.</p>
                <p><h4>Format Specefic Cracking:</h4> Once you have identified the hash that you’re dealing with, you can tell John to use it while cracking the provided hash using the following syntax: </p>
                <code>john --format=[format] --wordlist=[path to wordlist] [path to file]</code>
                <p>Example:</p>
                <code>john --format=raw-md5 --wordlist=/usr/share/wordlists/rockyou.txt hash_to_crack.txt</code>
                <div><h4>Tasks:</h4>
                    What type of hash is hash1.txt? Answer: md5
                    <br>What is the cracked value of hash1.txt? Answer: biscuit
                    <br>What type of hash is hash2.txt? Answer: sha1
                    <br>What is the cracked value of hash2.txt? Answer: kangaroo
                    <br>What type of hash is hash3.txt? Answer: sha256
                    <br>What is the cracked value of hash3.txt? Answer: microphone
                    <br>What type of hash is hash4.txt? Answer: whirlpool
                    <br>What is the cracked value of hash4.txt? Answer: colossal</div>
            </li>
            <li><h2>Cracking Windows Authentication Hashes:</h2>
                <p>NThash is the hash format modern Windows operating system machines use to store user and service passwords. It’s also commonly referred to as NTLM, which references the previous version of Windows format for hashing passwords known as LM, thus NT/LM.</p>
                <div><h4>Tasks:</h4>
                What do we need to set the --format flag to in order to crack this hash? Answer: nt
                <br>What is the cracked value of this password? Answer: mushroom</div>
            </li>
            <li><h2>Cracking /etc/shadow Hashes:</h2>
                <p>The <code>/etc/shadow</code> file is the file on Linux machines where password hashes are stored. It also stores other information, such as the date of last password change and password expiration information. It contains one entry per line for each user or user account of the system. This file is usually only accessible by the root user, so you must have sufficient privileges to access the hashes. However, if you do, there is a chance that you will be able to crack some of the hashes.</p>
                <h4>Unshadowing:</h4>
                <p>John can be very particular about the formats it needs data in to be able to work with it; for this reason, to crack <code>/etc/shadow</code> passwords, you must combine it with the <code>/etc/passwd</code> file for John to understand the data it’s being given. To do this, we use a tool built into the John suite of tools called <code>unshadow</code>. The basic syntax of <code>unshadow</code> is as follows:</p>
                <code>unshadow [path to passwd] [path to shadow]</code>
                <p>Example:</p>
                <code>unshadow local_passwd local_shadow > unshadowed.txt</code>
                <h4>Cracking: </h4>
                <code>john --wordlist=/usr/share/wordlists/rockyou.txt --format=sha512crypt unshadowed.txt</code>
                <div><h4>Tasks:</h4>
                What is the root password? Answer: 1234</div>
            </li>
            <li><h2>Single Crack Mode:</h2>
                <p>In this mode, John uses only the information provided in the username to try and work out possible passwords heuristically by slightly changing the letters and numbers contained within the username. Syntax:</p>
                <code>john --single --format=[format] [path to file]</code>
                <p>Example:</p>
                <code>john --single --format=raw-sha256 hashes.txt</code>
                <p>Note: if the hash in <code>hashes.txt</code> is: <code>1efee03cdcb96d90ad48ccc7b8666033</code>we need to change the file format that we’re feeding John for it to understand what data to create a wordlist from. We do this by prepending the hash with the username that the hash belongs to. Example: <code>mike:1efee03cdcb96d90ad48ccc7b8666033</code></p>
                <div><h4>Tasks:</h4>
                <br>What is Joker’s password? Answer: Jok3r</div>
            </li>
            <li><h2>Custom Rools:</h2>
                <p>We can make John follow certain mangling patterns when using single cracking mode. Custom rules are defined in the <code>john.conf</code> file.It is usually located in /etc/john/john.conf if you have installed John using a package manager or built from source with make. Syntax:</p>
                <ol>
                    <li>First line: [List.Rules:THMRules] is used to define the name of your rule; this is what you will use to call your custom rule a John argument.</li>
                    <li>We then use a regex style pattern match to define where the word will be modified; again, we will only cover the primary and most common modifiers here:
                        <ul>
                            <li><code>Az</code>: Takes the word and appends it with the characters you define</li>
                            <li><code>A0</code>: Takes the word and prepends it with the characters you define</li>
                            <li><code>c</code>: Capitalises the character positionally</li>
                        </ul>
                        These can be used in combination to define where and what in the word you want to modify.
                    </li>
                    <li>Lastly, we must define what characters should be appended, prepended or otherwise included. We do this by adding character sets in square brackets [ ] where they should be used. These follow the modifier patterns inside double quotes " ". Here are some common examples:
                        <ul>
                            <li><code>[0-9]</code>:Will include numbers 0-9/li>
                            <li><code>[0]</code>:Will include only the number 0</li>
                            <li><code>[A-z]</code>: Will include both upper and lowercase</li>
                            <li><code>[A-Z]</code>: Will include only uppercase letters</li>
                            <li><code>[a-z]</code>: Will include only lowercase letters</li>
                        </ul>
                    </li>
                     <ul>Note that:
                        <li><code>[a]</code>: Will include only a
                        <li><code>[!£$%@]</code>: Will include the symbols !, £, $, %, and @</li>
                    </ul>
                </ol>
                <div><h4>Tasks:</h4>
                <br>What do custom rules allow us to exploit? Answer: Password complexity predictability
                <br>What rule would we use to add all capital letters to the end of the word? Answer: Az"[A-Z]"
                <br>What flag would we use to call a custom rule called THMRules? Answer: --rule=THMRules</div>
            </li>
            <li><h2>Cracking Password Protected Zip Files:</h2>
                <p>We can crack password protected Zip files using the tool <code>zip2john</code> with the syntax:</p>
                <code>zip2john [options] [zip file] > [output file]</code>
                <div><h4>Tasks:</h4>
                What is the password for the secure.zip file? Answer: pass123
                <br>What is the contents of the flag inside the zip file? Answer: THM{w3ll_d0n3_h4sh_r0y4l}</div>
            </li>
            <li><h2>Cracking Password Protected RAR Archives:</h2>
                <p>We can crack password protected RAR Archives using the tool <code>rar2john</code> with the syntax:</p>
                <code>rar2john [rar file] > [output file]</code>
                <div><h4>Tasks:</h4>
                What is the password for the secure.rar file? Answer: password
                <br>What are the contents of the flag inside the rar file? Answer: THM{r4r_4rch1ve5_th15_t1m3}</div>
            </li>
             <li><h2>Cracking SSH Keys With John:</h2>
                <p>We can crack SSH protected keys using the tool <code>ssh2john</code> with the syntax:</p>
                <code>ssh2john [id_rsa private key file] > [output file]</code>
                <div><h4>Tasks:</h4>
                What is the SSH private key password? Answer: mango
                </div>
            </li>
        </ul>
    </li>
</ol>
