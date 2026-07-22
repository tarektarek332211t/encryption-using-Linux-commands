This project demonstrates how to encrypt and decrypt files using Linux commands.
STEP1: Create a file:-
  echo "Hello, this is an encrypted file" > encrypted.txt
    EXPLANATION: (echo) prints text
                 put the message in double qutes ("")
                 (>) prints message into the file after it
                 (encrypted.txt) is the plaintext file
    NOTE: using this command will automatically generate (encrypted.txt) file without using (touch) command
    
STEP2: Encrypt the file:-
  openssl enc -aes-256-cbc -pbkdf2 -salt -in encypted.txt -out encypted.enc
    EXPLANATION: (openssl) runs OpenSSL encryption tool
                 (enc) means encryption mode
                 (-aes-256-cbc) is an encryption algorithm
                 (-pbkdf2) is a cryptography algorithm
                 (-salt) adds a random SALT -which is a random group of elements- to improve secutity
                 (-in encypted.txt) specifies the input file which is unencrypted
                 (-out encypted.enc) specifies the output file after encryption
    NOTE: in the encryption command, the argument after (-in ) is the .txt file and the argument after (-out ) is the .enc file

STEP3: Decrypt the file:-
 openssl enc -d -aes-256-cbc -pbkdf2 -in encypted.enc -out decrypted.txt
   EXPLANATION: the decryption command is similar to the encryption one except some differences
                (-d) tells OpenSSL to decrypt the file
                (-in encypted.enc) specifies the input file which is encrypted
                (-out decrypted.txt) specifies the output file after decryption
   NOTE: in the decryption command, the argument after (-in ) is the .enc file and the argument after (-out ) is the .txt decrypted file
   NOTE: using this command will automatically generate (decrypted.txt) file without using (touch) command

STEP4: Verify the encryption and decryption process:-
  diff encrypted.txt decrypted.txt
    EXPLANATION: (diff) shows the difference between to file and it requires two arguments.
    NOTE: if there is no difference there will be no output


COMMANDS USED:-
  echo "text" > filename.txt
  openssl enc -aes-256-cbc -pbkdf2 -salt -in filename.txt -out filename.enc
  openssl enc -d -aes-256-cbc -pbkdf2 -in filename.enc -out filename.txt
  diff filename.txt filename.txt


FILES:-
  encrypted.txt
  encrypted.enc
  decrypted.txt
