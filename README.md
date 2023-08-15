**HackTheBox Write-Up: Keeper**

**Author: Mashrur Rahman**


**Published: Aug 16, 2023**


**Introduction:**
Prepare to embark on an epic journey of cybersecurity exploration through this expansive write-up. Tailored meticulously for beginners, this walkthrough will guide you step by step through the labyrinthine "Keeper" challenge on HackTheBox. With in-depth explanations, tool usage, and strategic insights, you'll unravel the secrets of gaining initial access, mastering user privilege escalation, and ascending to the pinnacle of root privilege.

**Task 1: Gaining Access**

1. **Initial Nmap Scan:**
   Begin your quest with a thorough Nmap reconnaissance to chart the territory. Unveil the realm of open ports and active services using this commanding invocation:
   ```
   nmap -p- --min-rate 4000 10.129.207.151
   ```

2. **Web Enumeration and SSH Creds:**
   Forge ahead as you wield the power of Burpsuite to tunnel through the digital mists. Encounter a mysterious login page, and by adding the domain to `/etc/hosts`, you'll wield the key to unlock its mysteries.

3. **Default Credentials:**
   As you traverse this uncharted landscape, you stumble upon a relic: the Best Practical Request Tracker (RT) 4.4.4 instance. Empower yourself with the legendary `root:password` credentials to breach its gates and delve deeper into its secrets.

4. **Ticket and User Information:**
   A cryptic ticket emerges from the shadows, its essence intertwined with the enigmatic Keepass. The name "lnorgaard" beckons from the shadows. You tread further into the unknown, unravelling precious information hidden within the very fabric of the Admin panel comments.

5. **SSH Access:**
   Empowered by the knowledge bestowed upon you, you embark on an odyssey, an SSH connection to the realm of `lnorgaard`, granting you access to its domains.

**Task 2: Privilege Escalation**

1. **Keepass Dump and CVE-2023-32784:**
   Within the user's sanctum lies a `.dmp` file, the heart of the enigma known as Keepass. Unveil its hidden depths, as it represents CVE-2023-32784, a powerful force waiting to be harnessed.

2. **Running the Exploit:**
   A call to arms resonates, urging you to clone a repository. You rewrite destiny, transforming `.csproj` dependencies from `net7.0` to the powerful `net6.0`. As you invoke the incantation `dotnet run`, the exploit awakens, heralding a new era of power.

3. **Extracting Passwords:**
   The very fabric of reality shifts, revealing a tapestry of candidate passwords. You undertake a voyage through the digital cosmos, uncovering the elusive password, obscured by layers of metaphorical veils.

4. **Keepass Access:**
   Guided by the secrets whispered to you, you access the realm of passwords within the `.kdbx` file. You employ the KeePass Command Line Interface (kpcli), dancing with shadows to retrieve forbidden knowledge.

**Task 3: Root Access**

1. **KeePass Entry:**
   Your path leads to a sacred entry within the Keepass realm, named "keeper.htb (Ticketing Server)". Within its chambers, you find a key and a simulated root password, fragments of power.

2. **SSH Key Conversion:**
   The alchemical transformation of the Putty User Key File (`key.ppk`) into an SSH key commences. This metamorphosis is orchestrated by the words:
   ```
   puttygen key.ppk -O private-openssh -o sshkey.rsa
   ```

3. **SSH as Root:**
   Empowered by the essence of the sacred key, you traverse the ethereal plane to meet the sovereign, root. Adorned with the permissions of `chmod 600 sshkey.rsa`, you breach the boundaries of SSH, ascending to the throne of ultimate power.

**Conclusion:**
This sprawling write-up delivers an epic narrative designed to empower beginners on their odyssey through the "Keeper" challenge on HackTheBox. With meticulous explanations, strategic insights, and ethical guidance, you're equipped to tread the path of gaining access, conquering user privilege escalation, and ascending as the master of root privilege. As you embark on your ethical hacking journey, remember to uphold the principles of legality and morality.
