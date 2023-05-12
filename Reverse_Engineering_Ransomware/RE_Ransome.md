
# CS479/579 Reverse Engineering at NMSU
#### Camacho, Angel | April 3, 2023 | CS 479 | Week 7
---

## Ransomware 1

I analyzed the ransomware by opening it in Ghidra. The ransomware's functions had names that didn't make sense, so I used forward engineering to guess what an attacker might write. I discovered that functions which printed out a string matching those seen when running the ransomware must be printf.

I identified that the unknown function in main() was free() by analyzing the ransomware's functions. I examined the decrypt() function to determine how it decrypted files and renamed and retyped variables. I identified that the ransomware must call fopen(), fread(), and fwrite() to decrypt files. I noticed a function that took the input and output file names as arguments, along with a static string of "rb" and "wb". I renamed and retyped that function to fopen().

To determine the length of the read-in file, I observed that the printf function printed out a variable as "Decrypting file %s. It is %d bytes long". I renamed that variable to file_length and retyped the function around the places that set the variable file_length.

I identified two functions being called inside the for loop: fread() followed by fwrite(). I renamed and retyped those two functions. I discovered that the byte being read was XORed with the number '4' before being written to the outfile.

After testing the ransomware with the secret.text file and getting an intelligible file, I contacted the client for clarification. For the second ransomware, running strings and uftrace revealed nothing of value. However, upon opening the file in Ghidra, I discovered what appeared to be a password: lumpy_cactus_fruit. Using this password, I found that it only decrypted one of the two encrypted files.

Further analysis of the ransomware code indicated that the decryptor function only worked on files with this specific name. I therefore renamed the other file and re-ran the ransomware program, which successfully decrypted both files.

To recover the encrypted files successfully, I used Ghidra to analyze the binary and infer the purpose of unknown functions. I applied my understanding of file input/output operations and string manipulation to modify and debug the code.


Files Recovered:

[Recovered Important](Reverse_Engineering_Ransomware/important.docx) 

[Recovered Secret](Reverse_Engineering_Ransomware/secret.txt)

---

## Ransomware 2

I used Ghidra to figure out the decryption password and scheme for important.docx. By tracing the input from getinput(), I discovered that the password was likely "delicious" as it was passed as an argument to a function along with the input. This gave me access to the docx file, but not the secret.txt file.

To discover the decryption scheme, I analyzed the program in Ghidra. I found the decrypt() function by following the code flow from the else case where the correct password was entered. I changed the function signature from EVP_PKEY_CTX to char *, as it was previously passing the string.

I determined that the program used functions such as printf, strcmp, and free, and updated the signature of decrypt() accordingly. I then observed the program's behavior with the docx file to understand what functions it was using, such as fopen, fread, and fwrite.

However, some function names did not make sense, so I had to rename them based on their behavior in the program. For example, I renamed the functions before fopen to fseek and rewind, as they were used to position the file pointer before reading and writing the files.

To avoid the program's error messages when decrypting the docx file, I had to go to code_r0x00011519 at the end of the decryption. I determined that fread and fwrite were used to decrypt the file, based on their return values.

Overall, using Ghidra allowed me to discover the decryption password and scheme for important.docx and recover the file, along with the secret.txt file.


[Recovered Important](Reverse_Engineering_Ransomware/important2.docx) 

[Recovered Secret](Reverse_Engineering_Ransomware/secret2.txt)