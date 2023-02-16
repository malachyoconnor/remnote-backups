- 
- **Lecture 2**  (File system security)
    - What is POSIX?―POSIX is a standard, describing unix-like operating systems.  
    - Supervisor mode 
        - What stops a normal user simply executing the same machine code commands as a root command?―Processor level support for determining privilege mode of operation. So 1-bit is set to decide if the processer is in supervisor mode or real mode.
    - Discretionary access control 
        - What is the bell-lapadula security policy?―Subjects and objects have a classification level, can read any objects at their security level and below bue cannot write to objects at a lower security level. 
**Write up, read down.**
        - Discretionary access control is where the creator of the file decides who can access the file.
        - This could be done by deciding for every user and ever file who can do what with the file. However, the resulting massive matrix is undesirable - thus instead users tend to be grouped.
        - In POSIX, what are the 3 user groupings? ↓ 
            - The owner of the file
            - The members of the files group
            - Everyone else
        - POSIX associates all users with an {{integer ID internally,}} where the administrator has {{id 0}}. The admin can create {{new users}} and impersonate {{other users}}. Furthermore, groups are {{named sets of users with integer IDs (internally)}}. Each user is associated with **at least **{{**one primary **}}{{group }}(listed in {{etc/passwords}}) and possibly more (listed in {{etc/group}})
        - The unix command id displays the current user, and the groups that user is a member of.
        - Each file has an owner and a group.
        - A directory is a special file that stores a mapping between file names and iNodes. Inodes contain pointers to the disk regions containing the contents of the files and metadata.
        - The same inodes can be pointed to by multiple directories. And thus the same file can be known under different names - these names are called **hard links **and can be created using **ln.** 
        - Permission bits 
            - An important piece of metadata stored in the Inode are the permission bits. These are 4 triplets - these sets of 3 bits are often represented as octal numbers. These bits represent **the user, the group **and **others**.  
            - r if you can read the file, w if you can write to the file and x if you can execute the file. If you have the permission the letter will be displayed.
            - For a directory, the permissions are subtly different - how?―r means you can list the files in the directory. w means you can add/remove/rename files in the directory (if you can enter the dir). x means you may access the metadata in the inodes and access the contents of the files (can see permissions and length of files) - e.g. you can enter the directory (execute it). 
            - How do you change permissions of files?―Using chmod. To add read permissions to user (u), group (g) and other (o) you can do :```c
 chmod go+r photo.jpeg
 chmod ug+r, og-w something.jpg
 chmod u=wrx, go=r code.py
 
 chmod 664 photo.jpg
 // sets user, group and other permissions using octal
     rwx
 6 = 110 | user
 6 = 110 | group
 4 = 010 | other
``` 
Chmod **only works** if issued by the owner of the file. It can also be executed recursively on a directory using -R.
        - OS permission check 
            - How does the OS compute permission checks? ↓ 
                - First, if the command comes from root it is automatically allowed. 
                - Then the OS decides which of the 3 triples applies (user, group and other) - it only checks that triplet (EVEN IF THE GROUP TRIPLET YOU'RE IN WOULD GIVE YOU MORE RIGHTS)
        - How do you change the file owner/file group?―chown bob:staff potato 
Sets the owner of potato to bob and the group to staff. **Note: **Only the owner can change the group, and only root can change the owner. 
        - What does the su command do?―This allows you to impersonate another user. su bob, opens a new shell under that user.
        - How do you list permissions?―ls -la
        - What is the principle of least privilege?―Every program and every privileged user should operate with the lowest level of privilege possible.
People who have root access use sudo, only using the privilege when necessary.
        - Describe setuid, what it's useful for and how it works.―setuid is used for more fine grained access controlled for users. The linux access controls don't generally allow you to say a user can only read/write a single line in a file.
setuid() sets the **effective user ID** of the process being called - unprivileged process can only set that to the real ID of the caller, otherwise **the effective ID is set to the ID of the file owner**. 
        - What does umask do, how do you use it and when would it be used?―This allows you to change the default file permissions. umask 022 means you disable write for group & other. It would generally be used in a startup file.
        - What are the default file and directory permissions?―666 are the default permissions for files, rw but no e for all. Directories get 777, everyone can do everything.
        - What is the sticky bit? ↓ 
            - For files -  this marks frequently used executable, to keep them in RAM rather than have them in secondary storage (more useful in the past).
            - For directories - the sticky bit handles shared directories. Consider, if Bob has w & x permission he can delete/rename Alice's files. The sticky bit means Bob can only access files he owns.
        - 
- **Lecture 3 **(Insecure Programs)
    - Attack Surfaces 
        - The attack surfaces describes all of the points an attacker could get into a system and where they could get data out.
        - find -L -uid 0 -perm -u=s -type f
        - What is stored in the etc/passwd file?―The user name, either a hash of their password or an x indicating their passwd is in etc/shadow. Their UID and GID, a comment field, the home directory and the login shell they use.
        - What's stopping you from putting a newline in chsh and creating a new user with UID 0―chsh is prudent enough that it only allows one of the inputs listed in etc/shells.
        - What is the attack surface of this program and what could you use it for? ```c
#include <stdlib.h>
void main() {
	system("ls");
}
```―The path the program is executed from. To make use of this program you could simply change the path to somewhere you can access, create another "ls" program that performs privilege escalation and then run this program. As it only runs ls in a console.```c
 export PATH=.:$PATH
 ./demo-ls
```
        - What could you do for this program: ```c
void main(int argc, char* argv[]) {
	char command[80];
	sprintf(command, "/usr/bin/cat %s", argv[1]);
	system(command);
}
```―They've used the countermeasure of specifying a directory (with a space after the cat so you cant simply ../).  However as system just uses the command line, we can simply do : ```c
 ./catprogram testing.txt;sudo /bin/sh
```
        - A huge amount of attacks are possible when an attacker can trick a program into interpreting data as commands. 
    - Environment variables 
        - What is dynamic linking?―Dynamic linking is the alternative to static linking - in which libraries are included in the binary. In dynamic linking, the libraries are found in your filesystem at runtime and linked with the rest of the executable. This allows for easy updating of libraries and reduces the size of the binary.
        - There are environment variables that allow you to manipulate the dynamic linker. LD_LIBRARY_PATH, LD_PRELOAD sets a list of programs to be loaded first (whether the program requested them or not). These are commonly used for debugging without having to recompile - however we could clearly add arbitrary code. Therefore, these paths can only be set if the effective uid is the same as the real id.
        - 
    - 
- **Lecture 4 **(Buffer overflow)
    - Memory arrangement
        - When you declare two variables at once, c is not obligated to place them next to each other in memory - it could insert gaps, swap them etc.
    - Stack frame x86
        - In what order do we push items into x86 stack frames?―First we push the parameters of the function in reverse order - so when we read **up **in memory, we encounter the first parameter first etc.
Then we push the return address.
Then we push the previous frame pointer
        - What do the stack pointer and frame pointer point to?―The stack pointer points to the very bottom of the stack. Even below the local variables of the final stack frame.
The Frame pointer points to the "bottom" of a stack frame, above any local variables of the function. I.e. it points to it's own location, remember it is used to provide an offset **that doesn't change**.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/0vBJgDfKrJ6vU233zvrDj_Hb8uqx_QLMUEVXbmFxS3oJR47aylkeUEGMcKWn8lszyQoRyCDlvwVJrdActcGM3dzVU-Adzynj6asonYpmeccez2RaRexYDWA31VzUM4f1.png) 
        - How does a buffer overflow (which executes code) work?―First you overflow a buffer in the stack and smash the stack. This overflow must flow into the return address of the stack frame.
Then the return address must be overwritten to point at some machine code payload which will be executed.
    - NOP Sled 
        - What is a NOP sled?―A NOP sled is used in a buffer overflow attack and contains your malicious code followed by a number of NOP commands. A NOP command simply "does nothing" and then moves the Next instruction register up by 1.
These mean you don't have to point to the exact location of your payload - which is good because we don't know exactly where in memory it'll end up.
    - Stack spraying 
        - What is Stack spraying?―This is a method for dealing with uncertainty about the structure of the stack frame - to combat this you overwrite all the registers in a range where the stack pointer could be.
    - Countermeasures 
        - Languages other than C or assembler will do bounds checking. 
        - What is the Stack canary approach?―Defender stores a special marker between the local variables and the return address. Then when the function returns, check if the marker has been changed.
This is made more difficult for the attacker by making the canary a random value.
        - A shadow stack is―a method of keeping two stacks and keeping them in sync - then comparing them to see if they are the same.
        - What is ASLR?―Address space layout randomization. Randomly allocate the start segment of everything in memory.
Aren't that many bits of entropy available, so brute force is feasible.
    - 
- **Lecture 5 **(Return to libc)
    - What does disabling stack execution disable?―Stops you from putting your shellcode in the stack to be executed, you'd have to point to executable code elsewhere.
    - In return to libc, what do we change the stack frame to point to?―We point to something in the associated C libraries, like system. Which will run with the priviledge of the program. 
    - What do we need to find for a return to LIBC attack? ↓ 
        - Find the address of the required system call
        - Pass the intended parameters in the way the system call expects
        - (optionally) clean up afterwards to ensure the process doesn't crash afterwards
    - Structure of the stack 
        - Describe what happens on the stack when a caller invokes a subroutine (called the prologue)  ↓ 
            - First push the parameters to the function in reverse order. (note that every time something is pushed, the stack pointer is incremented).
            - Then when the caller invokes the function, the call machine code instruction pushes the return address on the stack.
            - The callee (the subroutine) then pushes the base pointer onto the stack - this points to the previous stack frame.
            - The callee then updates the EBP to point to that location.
            - Then the stack pointer is moved to accommodate the local variables.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/NMonqGB5ZInWgFwlSoFMg6wGao4QesD999MGcZAabagAqxzXXCdpzFtk8euFtFvL6fIc5aj8f-jD4woV9r_jU_gwyntUFeddJcVn1DnrbMEpL-SFru5UlXsKsAdxaGnu.png) 
        - Note in Intel opcode we have:
move **dest source** 
While in Unix we have
move **source dest** 
        - Describe what happens at the end of a subroutine (the epilogue).  ↓ 
            - First the base pointer is copied into the stack pointer. Effectively deleting the values below the base pointer. 
            - We then pop the previous frame pointer into the base pointer. (Which also moves the stack pointer up)
            - We finally call a return, which pops the return address into the instruction pointer. Transferring execution to that address.
        - In our soon to be smashed stack, we have the following layout:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/p9pMYFfdEBz87gIsyocaHXV6O1teTMiYxhNmkb6uporeohSknSwjuj434TD4OwsAVOSuV3lXmNGLJZgGohfVSMURydBUdF0al0P4o2VdHfDLxe3bmhd54_nogvax3HVZ.png) 
What do we need to put in the first 3 slots? ↓ 
            - We know we need the address of system() in the RA - that's how we're calling system. 
            - First note that when this function goes to return, the ESP will be popped into the EBP leaving:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/PiEYEb2wMa0qULmXWHTZIapL3Cn2GI31n48f6Ev3BCsuFYwrIinVES9GZo0IMkRqg4Wd7zFVmO9rs_84w0yq-8M_HF62yII_Ldd5uDpXI6wRaiQp-O5fkm3gamrFBbwK.png) 
            - System has 1 argument, and will look for that at the top of the stack meaning in order to access a stack we need:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/YgXeXTNHXY7TbxMNdLqfxlSGMGXLRA_7BCkMKMhTUAnVVnvxlsg8xa9V7ESIYpU387OwMt2VaTXY9naY5c1APJtMybXBdECE-NW9P_tJpcYN_um_eXKuxa0VJTZRTQbI.png) 
            - Finally **because system only takes 1 argument **it will look for the return address just below that. Meaning we need out exit() function there to ensure a seg fault doesn't occur: 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/d-fvugakIsEo_xmImnPS2o09Q-RmW0J19UThoo_i4JQkAp-RBwO_Rq6jnP2bUGXybk7rn7U0Mk99uvRkpGVS119XWrCfzIvsfAIL1HvJl9U30rwt--64IT-qfvV5wSCj.png) 
    - 
    - 
- **Lecture 6 **(SQL injection)
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/DjmnMJP99UvkuDeRxBlv0WoCLUeLhPDDoozX-icQrHdFovwXPDdpnw-Np-eOILIe7Tng1QVHGGrVEhgTT4X4gLTZTtjcZZzo-9tdrDQyvvc8pMbIGTgd8R6YLv0nucOD.png) 
    - The double hyphen space comments out the rest of the input.
    - How can we solve SQL injections―We can precompile the code sections, and leave space for what can ONLY be data - i.e. do no parsing on the code.
- **Lecture 7 **(Passwords)
    - Authorisation 
        - 3 main factors Confidentiality, Integrity, Availability.
        - Authentication can be unidirectional or bidirectional (each proves their identity to the other).
        - The verifier should check something you know, have or are.
    - How do passwords work 
        - What are the underlying assumptions of passwords? ↓ 
            - No one but me knows my password.
            - No one can guess it.
            - The verifier can verify my password.
        - How are hashes used with passwords?―Instead of storing a plaintext password, store a hash of the password and check that each time. The hashed password is called a "digest".
        - How can an attacker use hashed passwords?―With a long list of hashed password, hash guessed passwords and match them to users.
        - If Alice notices Bob has the same digest as her, she can log into Bobs account.
        - Describe "salting" a password―When a password is created, a random string (a salt) is added on the end before hashing. Then the digest and the salt is stored in the passwords file.
This means the attacker would have to guess the password AND the salt (or try all salts with all passwords).
This helps stop lookup attacks, where the attacker runs through pre-generated hashes. For a salt of length k, the attacker must store 2^k more bits.
        - What is key stretching?―Using the hash function hundreds of times for each password - making cracking the passwords take hundreds of times longer.
        - What are lookup tables of passwords?―Massive lists of pre-generated hashes (without salts).
You can run through these asynchronously and tear through them.
        - What are rainbow tables?  ↓ 
            - They are a method of reducing the space complexity of storing loads of hashed passwords.
            - We have a hashing function $h : P \mapsto D$ (maps passwords to digests.). Then imagine some $r : D \mapsto P$ which maps digests to passwords.
However, it does so somewhat randomly - jumping somewhere else in the password space. 
            - We first generate passwords and digests in a large table, we then repeatedly apply $h$ and $r$ to a digests in that table. Resulting in jumps around the table. We compute l "hops" and store a start and end digest in our table.
            - We repeat that process until our table is exhausted.
            - Finally, when we encounter a password - we first check if its digest is in our new table (under the final digest column), If so we work forwards from the start digest to get the associated password.
            - If the password is not, we apply h and r to get a new digest and check that. We repeat this process $l$ times, and if we never find our password we know it was never in our original table! If we do identify the chain, we need to work forward from the start digest again
    - How passwords fail
        - Complex passwords. Passwords you don't write down. Passwords with upper and lowercase letters - each one defensible on it's own, but too hard for users when combined.
        - Users reuse passwords, so if any site gets cracked then their vulnerable on all other sites. Then results in needing users to use different passwords for every site - results in many passwords where we can't remember all of them.
        - How do online password attacks differ from offline attacks?―Online attacks are slower (need to send a request) and a large number of failed login attempts should alert an admin.
This points to the fact that admins should secure the password file, rather than imposing draconian rules on the users password.
    - Why passwords still with us 
        - What are moral hazards? How do they apply to passwords?―Moral hazards is when an actor increases it's risk factor because it doesn't bear the full responsibility of that risk. 
E.g. if a big company takes a risk, it'll get bailed out by the bank.
Passwords are easiest to deploy for a website, and they don't bear the usability issues of them. Marginal cost per additional user zero.
        - Issues of biometrics ↓ 
            - replay attacks.
            - Biometrics are not private. Need a liveness check (e.g. say this word, must makes it unsuitable for unsupervised login).
            - You can't change your biometrics, if they get leaked you're fucked mate. 
        - What's the problem with single sign on systems?―Usually not "single", e.g. we can use raven to sign onto cambridge systems - but need other services to sign onto other systems.
    - 
- **Lecture 8 **(Cross-site request forgery)
    - Web Cookies 
        - In HTTP, distinct requests are independent. But we want to create sessions, were state is recorded. 
        - Cookies are stored instead, which record data about the user - also have a TTL. Then whenever the user makes a new request, the cookie is attached to the message (assuming the cookie has not expired).
        - However, if the server doesn't store any data - we can manipulate the cookie. e.g. Can we manipulate the price?
        - What is a sessionID, how does it relate to cookies?―A sessionID is a unique identifier for a session on the website. The server stores the session data and the **cookie **stores the sessionID. 
    - Phishing 
        - Describe HTTPS, how does it help against Phishing?―HTTPS is a transfer protocol that encrypts your communication and also confirms a website server is who they say they are. Via a certificate. So a fake hsbc-website.org would not have the HTTPS. 
        - Multi-factor authentication is another countermeasure.
    - CSRF 
        - How does a CSRF (Cross-site request forgery) attack work?―The attacker crafts a link which will send a request to their bank (for example) initiating a transfer into the attackers account. If the victim is logged in, then the login cookies will be attached and the transfer will go through.
You don't even need a link, could be a 0x0 pixel image in your email.
        - What's the difference between GET and POST? ↓ 
            - In a GET request, the values of fields are included in the URL e.g. 
GET https`:www.bank.com/get?amount=5&to=Charlie` 
            - In a POST request, the parameters are encoded as part of the request body of the HTTP request. You don't see it in the address bar.
Might just have the url `https://www.bank.com/pay-action-post ` 
        - Describe counter measures for CSRF ↓ 
            - The webserver could only honour requests coming from it's own site - however HTTP is stateless so they can't tell that. 
            - The browser **can **tell what website you're accessing a page from. So it uses the following Schemes:
            - The **referrer header**: Mention the website the user sent the request from. However, it is optional and is often disabled - can lead to false positives. 
            - The **same site cookie attribute**: Set an attribute to the cookies 
            - The **secure token**: Which can be implemented at the web application level - and can thus be deployed without waiting for browsers to standardize. Every web app would need to reimplement.
The server embeds a secret with every form, the attacker cannot see it as they haven't seen the form.
The timestamp is also sent, allowing the server to recompute the secret.
    - 
- **Lecture 9 **(TCP attacks)  
    - Packet Sniffing 
        - The two endpoints connect to the network using a NIC, the physical medium is usually shared with other computers on the LAN. Usually the NIC would only accept the messages addressed to the NIC. But we can enable promiscuous mode which forwards all received packets at the NIC to the kernel.
        - The kernel can filter based on some criteria. This is written using BSD packet filter.  
    - Spoofing Packets 
        - Using raw sockets, we can write into the header. And claim a message comes from a different host.
    - SYN flooding 
        - Sequence of ACKS:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/vQXz4GTquDH8p4bLn8vNk7C6uSqOUQPyK9bwcElvZBqEdY4MrAtXN8xUiICu9VUy5e3c_U6IcTWC4BV0sAYA6IUT0SSEwo1xeWb_spRwguOu1eavmhxmcT1OtwU6DdMM.png) 
        - Bob discards an ACK packet if it doesn't adhere to it's previously sent syn and ack values. The values of x and y are stored in a TCB by Bob - Bob resends the SYNACK a few time and finally deletes the TCB if he doesn't receive an ACC.
        - This list of TCB's is finite. So SYN flooding works by  
        - What is SYN flooding and how does it work?―It is a denial of service attack. It works by flooding a user with SYN messages (requesting to open a TCP stream) and for each one the victim will allocate a TCB (a transmission control block). When no more TCBs can be allocated, the attack has succeeded.
The attacker must spoof their address to ensure a firewall cannot stop them.
        - Describe the SYN cookie defence. ↓ 
            - This works by no longer allocating a TCB - defeating the SYN flooding attack.
Instead all the information is embedded in the ACK number of the final ACK sent by Alice. 
            - Bob simply makes the ACK he sends a function of the values in the packet (and this function is secret, only he can compute it) - using the source address, port number and sequence number  
            - Then when Alice sends a SYN packet, Bob would expect the y+1 value to match the computed value. So he simply runs the computation again and tests it. A malicious party cannot spoof this, as they do not know Bob's function.
        - Describe a different defence, without SYN cookies―We set aside some privileged space to store TCB's of hosts who have already connected to Bob in the past - so they are not affected.
So the attack only effects new hosts.
    - TCP Reset Attack 
        - Recall the usual way of closing a TCP connection:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Zfx8LiGQwk72Y_EMI_QMGUu5i_pGuevqD3v2rQO2WK6QwCe06McqnxFkYZaXyzv5GbBflwk_sReHZCLdzV3LqyjPVIWQm3EQswGTwhrzOyLNtXQBnxNiElcseO6p21tU.png) 
We can also reset.
        - What is a TCP reset attack and how does it work?―Alice sends a reset attack to Bob and spoofs the message as if it came from Dave.
She must fill in the correct ports, addresses AND sequence and acknowledgement numbers.
    - TCP session hijacking 
        - What is TCP session hijacking and how does it work?―We sniff the connection of an outgoing message and instead of replacing it with a reset - we send a new set of messages with correct ports, addresses, sequence and acknowledgement numbers AND we send a new command to Bob. 
E.g. if Bob is a fileserver, we send a command to delete a certain file.
    - 
    - 
- **Lecture 10 **(Human factors in security)  
    - Users are not the enemy
        - Insufficient communication with users, results in unusable systems. 
        - Users forced to comply with securities incompatible with their usual work practises will look for workarounds.
        - The claim that users are never motivated to behave securely is wrong. Treat the users as stakeholders and they will provide feedback and usable security mechanisms. 
    - The Compliance Budget 
        - Users have a finite supply of goodwill (compliance budget) every act of following an annoying security policy will reduce that goodwill. Any further acts will result in the user constructing workarounds.
        - Manage the compliance budgets **wisely**. Harassing on many small security issues may result in the user failing to follow more crucial security requests. 
    - Prospect Theory 
        - How does your utility of moneye grow as your wealth increases.―The utility of money does not grow proportionally to the amount of money you have.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/e6ALH7tRr-Nsxh5ViavnOfLt99S6skZ74rWVvBHtG-xujH5Hq-m24Rlo9mJGNb5L1cxlXKwww-BdCCN33XM2BaiD7H48m3LeKQl4Uj9mdrOry7ARUWEWBtH9JYSIXmrJ.png) 
Instead it grows logarithmically.
        - What is utility theory?―Because you're utility of wealth grows logarithmically, the rational outcome of a question like:
$$\text{would you risk £100 to win £101?}$$ 
should be based on the utility of each outcome.
e.g. the increase in utility in winning 101 dollars is far less than winning 100 dollars.
So the expected utility is a loss.
        - Where does utility theory fall down?―People are often averse to gambling to secure a gain, but are willing to gamble to avoid a loss.
People are significantly more sensitive to losses. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/3w2HtTbD3pdtLisfNi7EQyQErLZjD6XpMYqW9s6zwcta21rn8UNBcAQe4TkAqeIGvlra9-Mi3eMSirjc1h41ZIoC69yMyAlZYIvTO7OcroBs4lXDfk4MCnw1DHLDeZLt.png) 
    - Understanding Scam victims 
        - Scam barman by taking advantage of him scamming customer out of large reward. E.g. barman says the reward is £50 when it's £200. He advances the £50 and never hears back from the person offering it.
        - The dishonesty principle is―People are not likely to come forward to having being scammed, if they've acted dishonestly themselves.
E.g. Nigerian scams where they want you to help them launder money.
        - Need-and-greed - urgent cravings and greed used.
        - Time principle - the fact that an opportunity will disappear soon means the victim will use fallible heuristics quickly.
        - Almost all scams can be reduced to a handful of principles. 
    - 
    - 
- **Lecture 11 **(Viruses, worms, Trojans and quines)
    - Malware 
        - Any software that will damage software or networks. 
    - Viruses 
        - A **virus **attaches itself to executable, and replicates itself affecting other executable. They lie dormant and eventually deploy a payload. 
        - Initially the antivirus companies looked for {{byte sequences}}. Virus writers started {{encrypting}} their virus code, hiding it differently {{at each infection}}.
Antivirus writers then look for the signature of the {{decryption engine }}- which needed to remain in plaintext.
Virus writers wrote polymorphic decryptors, which themselves are morphed.
    - Worms 
        - Worms doesn't infect executables, it simply sends copies of itself through the network. 
    - Trojans 
        - Propagates through some kind of social engineering - hide the software as something else and trick the user into launching it.
    - Spyware 
        - Sits on the attackers machine and logs data. Could log key presses, camera data etc. Usually designed to be stealthy.
    - Adware 
        - Malware that shows advertisements on your screen.
    - Ransomware 
        - Encrypts your file until you pay some ransom, at which point they decrypt it.
        - What's the order ransomware uses of keys to encrypt your files?―First it encrypts your files with a key, then it encrypts that key with the attackers public key.
It then asks the user to send the encrypted key to the crook, who promises to decrypt it.
    - 
- **Lecture 12 **(Lockpicking)  
    - Pin tumbler lock 
        - Pins get placed in holes, key pushes up the pins to different heights. Driver pins pushed by springs above sit in the holes, and the pins force the driver pins to be flush above the barrel - allowing the key to turn the barrel.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/2aqyZ4uNSflzGZCByGliHBHE7gbRhof5Jmkxq6o73EMYTEYOG9Efp8_5GPwMU6JlF_iobkhq68ryChi0zG8ovu9z97yecWpExRCp09L0ts_Ocpf-aNOA1IwJAwezORa2.png) 
        - Describe single-pin picking―We apply torque to the lock, and find the pin which is resisting the housing the most. We then move this pin until it's flush and continue.
The attack is $O(s^2)$ where s is the number of pin stacks. 
        - Describe Raking?―Apply torque and simply rake a tool back and forth in the barrel. Applying single-pin picking at high speed. Needs little dexterity.
        - Describe bumping―Prepare a skeleton key with the maximum depth in every key-way. Insert it into the lock, apply tension and smack the key. This knocks the pins and the driver pins up, and if we turn at the right time they return to their flush position as we turn the key.
        - Give methods to protect against raking and lock-snapping  ↓ 
            - For raking, include driver pins who's springs are of various strengths. Or include pins of strange shapes.
            - For lock-snapping insert a sacrificial section, which will break first.
    - Privilege escalation on mechanical master-lock systems 
        - Describe how master keys work on mechanical locks?―Insert multiple pins into a single pin stack, so an employees key will push all of the pins up while the master key would push some of the pins out and allow the barrel to turn.
E.g. consider a lock with pin heights 34738, for the master key 44217 to work - the lock must pins of size (1+3) (4) (5+2) (2+1) (1+7)
Then the lock can be added by both.
        - However, note that at each pin we've now got **two possible choices of key height**. Resulting in $2^4 = 16$ (Pin 2 only has one cut) - so there are 14 more keys that can open this lock.
        - Describe privilege escalation in master-keys―Given a differ key, we can find the master key by the following. First form the keys:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/vZEvYmC-WgSJ06Fp1b3JkvBGsTaybO-1cz7ueH-QipUD3sFynKSDfQUieKumH8MW1BYeUP-rP_Z1pD7A-FSksjWagL3hF-jX6iiXwmAVgscRLJn3GDFU-2tZlQDJyYcl.png)
Then try file down to height 9, then 8 then 7 etc. Until the lock turns for each key.
We then know the height of the master key. 
    - Security is risk management 
        - Identify the motivation of attackers (based on value), identify the possible attacks and the weaknesses in your system. Then find the possible mitigations against these attacks.
We then consider the costs of the safeguards vs loss of the items.
    - 
    - 
    - 
- 
- Assorted flashcards
    - You cannot create users or leave a group without root permissions.
    - You can write to open file descriptors if you have the write permissions.
- 
- 
