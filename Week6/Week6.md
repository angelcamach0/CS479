# CS479/579 Reverse Engineering at NMSU
#### Camacho, Angel | Feb 14, 2023 | CS 479 | Week 6
---

In this week we solved three easy "crackmes", the extraction password for each of these is 'nmsu_re'.

For the first ezcrackme I used uftrace with the flag -a which is supposed to print out any strings it observes. 
Here is my terminal out put:
![ezcrackme1](./Screenshot%20from%202023-03-24%2010-34-35.png)
As one can observe in the above screen shoot you can see a line that compares the users input with another string.
This string being "picklecucumberl337" which is a big indicator that that may be the correct password.
Which after testing it was infact the password.


For the second ezcrackme I also began my analysis with uftrace also witht he -a flag, here is my output.
![ezcrackme2](./Screenshot%20from%202023-03-24%2010-49-44.png)
As we can observe once again our test input string is compared with another string (in this case I compared the correct password)

I also ran strings on the file, which also helps print out strings in the file, I did this because sometimes we can't relly on one tool to always get us the answers we want.
Command ran: strings -n 4 easy_crackme_2 | grep -v "_" | grep -v "\."
flag -n specifies string length min, we pipe the output and use grep flag -v to remove strings that use underscore "_", and also remove strings that start with periods ".".
This was done to remove excess ammount of strign and be able to observe output clearer.
![ezcrackme2](./Screenshot%20from%202023-03-24%2011-12-28.png)


For the third crack me I started with with the tool strings, with the same command but specified the different file.
In this case I observed that there were two strigns of interest, strawberry and kiwi. Next I procedded my analysis with uftrace and tested out of curiosity the password strawberrykiwi.
![ezcrackme2](./Screenshot%20from%202023-03-24%2011-44-11.png)

---

During this week we also practiced finding where to start in a crackme that involves several functions. Remember the strategies we have to find where to get started:

    Identify the source and sink - where does execution start and where you want to get to?
    Work backwards from the sink towards the source
    Read functions from the end back to the beginning
    Use C standard library functions to figure out what variables 
