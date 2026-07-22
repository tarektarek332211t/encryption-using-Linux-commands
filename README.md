# Linux File Encryption using OpenSSL

This project demonstrates how to encrypt and decrypt files using OpenSSL commands in Linux.


## STEP1: Create a file:-

  ```bash
  echo "Hello, this is an encrypted file" > encrypted.txt
  ```

# EXPLANATION: - `echo` prints text
               - the message is written inside double quotes ("")
               - `>` redirects output to the file after it
               - `encrypted.txt` is the plaintext file
               
  *NOTE*: using this command will automatically generate (encrypted.txt) file without using (touch) command
  
    
## STEP2: Encrypt the file:-

  ```bash
  openssl enc -aes-256-cbc -pbkdf2 -salt -in encrypted.txt -out encrypted.enc
  ```

  EXPLANATION: -(openssl) runs OpenSSL encryption tool
               -(enc) means encryption mode
               -(-aes-256-cbc) is an encryption algorithm
               -(-pbkdf2) stands for Password-Based Key Derivation Function 2 (PBKDF2), used to derive a secure encryption key from the                            password
               -(-salt) adds a random value (salt) before key derivation to improve security and protect against rainbow table attacks
               -(-in encrypted.txt) specifies the input file which is unencrypted
               -(-out encrypted.enc) specifies the output file after encryption
               
  *NOTE*: in the encryption command, the argument after (-in ) is the .txt file and the argument after (-out ) is the .enc file


## STEP3: Decrypt the file:-

   ```bash
   openssl enc -d -aes-256-cbc -pbkdf2 -in encrypted.enc -out decrypted.txt
   ```

 EXPLANATION: the decryption command is similar to the encryption one, with a few differences
              -(-d) tells OpenSSL to decrypt the file
              -(-in encrypted.enc) specifies the input file which is encrypted
              -(-out decrypted.txt) specifies the output file after decryption
              
 *NOTE*: in the decryption command, the argument after (-in ) is the .enc file and the argument after (-out ) is the .txt decrypted file
 
 *NOTE*: using this command will automatically generate (decrypted.txt) file without using (touch) command
 

## STEP4: Verify the encryption and decryption process:-

  ```bash
  diff encrypted.txt decrypted.txt
  ```

  EXPLANATION: (diff) shows the difference between two files and it requires two arguments.
  
  *NOTE*: if there is no difference there will be no output



### COMMANDS USED:-

  echo "text" > filename.txt
  openssl enc -aes-256-cbc -pbkdf2 -salt -in filename.txt -out filename.enc
  openssl enc -d -aes-256-cbc -pbkdf2 -in filename.enc -out filename.txt
  diff filename1.txt filename2.txt



### FILES:-

  encrypted.txt
  encrypted.enc
  decrypted.txt



### Security Concepts Learned:-

- Symmetric Encryption
- AES-256-CBC
- PBKDF2
- Salt
- OpenSSL
- Linux File Redirection
- File Integrity Verification
