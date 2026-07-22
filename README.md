# Linux File Encryption using OpenSSL

This project demonstrates how to encrypt and decrypt files using OpenSSL commands in Linux.


## Step 1: Create a file

  ```bash
  echo "Hello, this is an encrypted file" > encrypted.txt
  ```

  ### Explanation
   - `echo` prints text
   - the message is written inside double quotes ("")
   - `>` redirects command output to the file
   - `encrypted.txt` is the plaintext file
               
  > **Note:** This command automatically creates the `encrypted.txt` file without using `touch` command
  
    
## Step 2: Encrypt the file

  ```bash
  openssl enc -aes-256-cbc -pbkdf2 -salt -in encrypted.txt -out encrypted.enc
  ```

  ### Explanation
   - `openssl` runs OpenSSL encryption tool
   - `enc` means encryption mode
   - `-aes-256-cbc` is an encryption algorithm
   - `-pbkdf2` stands for Password-Based Key Derivation Function 2 (PBKDF2), used to derive a secure encryption key from the                            password
   - `-salt` adds a random value (salt) before key derivation to improve security and protect against rainbow table attacks
   - `-in encrypted.txt` specifies the input file which is the plaintext file
   - `-out encrypted.enc` specifies the output file after encryption
               
  > **Note:** In the encryption command, the argument after `-in ` is the .txt file and the argument after `-out ` is the .enc file


## Step 3: Decrypt the file

   ```bash
   openssl enc -d -aes-256-cbc -pbkdf2 -in encrypted.enc -out decrypted.txt
   ```

 ### Explanation
  - the decryption command is similar to the encryption one, with a few differences
  - `-d` tells OpenSSL to decrypt the file
  - `-in encrypted.enc` specifies the input file which is the encrypted file
  - `-out decrypted.txt` specifies the output file after decryption
              
 > **Note:** In the decryption command, the argument after `-in ` is the .enc file and the argument after `-out ` is the .txt decrypted               file
 
 > **Note:** This command automatically creates the `decrypted.txt` file without using `touch` command
 

## Step 4: Verify the encryption and decryption process

  ```bash
  diff encrypted.txt decrypted.txt
  ```

  ### Explanation
   - `diff` shows the difference between two files and it requires two arguments.
  
  > **Note:** If there is no difference there will be no output



## COMMANDS USED

  ```bash
  echo "text" > filename.txt
  openssl enc -aes-256-cbc -pbkdf2 -salt -in filename1.txt -out filename1.enc
  openssl enc -d -aes-256-cbc -pbkdf2 -in filename1.enc -out filename2.txt
  diff filename1.txt filename2.txt
  ```



| FILES | Description |
|-------|-------------|
| `encrypted.txt` | Plaintext file |
| `encrypted.enc` | Encrypted file |
| `decrypted.txt` | Decrypted plaintext file |



## Security Concepts Learned

- Symmetric Encryption
- AES-256-CBC
- PBKDF2
- Salt
- OpenSSL
- Linux File Redirection
- File Integrity Verification



## What I Learned

Through this project, I learned:

- Basic file encryption and decryption using OpenSSL.
- How AES-256-CBC works as a symmetric encryption algorithm.
- The purpose of PBKDF2 in deriving secure encryption keys.
- The importance of using salt to improve password security.
- Linux file redirection and basic terminal commands.
