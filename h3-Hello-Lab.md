# h3 Hello Lab

## Task X 

### Installing Debian on Virtual Box 

1.Download the current version of the installation .ISO file. The one linked is for an old version. *I used debian-live-13.3.0-amd64-cinnamon.iso*

2. Install Virtual Box. As I run Windows 11 I used the installer linked for my OS

3. Create a new virtual machine by clicking new

4. Select the folder for the VM. *I recommend crea

5. ting a folder specific to this VM to keep the files organised. Name them after the system that you are testing to be able to tell them apart. I will put mine for example into the folder "/infosec/Network"*

6. Give the VM a distinctive Name *Mine will be named Portscan, as that is what I plan to test with this VM*

7. Select the ISO File that you downloaded.

8. Uncheck "Proceed with Unattended Installation" *This enables selecting the OS Version*

9. Select the OS Version of the file that you downloaded *In my case it is an amd64 version, so I choose the 64 bit version of Debian*

10. Open section "Specify virtual hardware"

11. Choose an amount of RAM and number of cores acording to your host system *I have 32GB of RAM and 16 CPU cores available, so I choose 16 Gb of RAM and 8 cores. If you are planning to just run VM at a time,
  you can give this one plenty of resources. I chose for example 50% of what is available.*

12. Open the section "New virtual hard disk"

13. Choose the size of the virtual hard disk *In my case the standard setting was 20 GB, but I chose 100Gb. You can set something much higher depending on your host hardware,
  as the space is only going to be used up once you actually store that amound of data in the VM.*

14. Finish the setup 

15. Open the Virtual machine

16. Choose to run the live system *You could normally also just run the installer directly, but we want to test functionality first and the installer in the live system can be more comfortable*

17. When the live system start up is complete open the terminal and send a ping to test that the network tunnel is functioning. *You can cancel the ping with ctrl + c. I send a ping to 1.1.1.1, which is a Cloudflare server, mainly because it is easy to remember. 
You could choose any IP-Address that is reachable from your local network* 

18. Start the installation by clicking on the Install Debian icon

19. Choose the installation language

20. Choose the correct time zone *You can click the map for an easier selection.*

21. Choose the keyboard layout corresponding to your host system keyboard

22. Choose the to either use the whole disk as one partition and click Erase Disk or manually partition the drives that you want *I dont need several partitions so I choose Erase disk*

23. Click next and set up a user account *I tend to just use my name for the user account. For the computer name I'd recommend to name it same as the virtual machine, but add a VM-prefix to clearly mark this computer as a VM in the network.
In my case I will name it VM-Portscan*

24. Setup a password *If you are testing security features set a strong password, to simulate a real world case. If you are testing something that requires you to type in the password a lot and does not concern security choose something short and easy to type.*

25. Click install to start the installation *Depending on your host system and the ressources of the VM, now is a good time to go get something to drink or just stretch your legs as the installation can take a moment*

26. Log into the account

27. In Virtual Box click on "Devices" and then on "Insert Guest Additions CD Image..." *This will install drivers, that will for example size the screen correctly and allow copy and pasting between host and virtual machine*

28. Run the installer when it pops up

29. Restart the VM *That's it you are done*

### Command line basics

There are many commands that are practical to know and the most basic are cd, ls, and pwd.
**cd** lets you change the directory that you are in
***ls** lists all the files in the current directory
***pwd** tells you what directory you are currently in

**sudo** gives elevates the access rights of the command that you are sending. 


## Task A 

### Show that network access is functional
<img width="799" height="523" alt="image" src="https://github.com/user-attachments/assets/0842af43-5966-4015-94eb-310fb96a895e" />

### Show that the network is non-functional
<img width="903" height="564" alt="image" src="https://github.com/user-attachments/assets/bf18032b-58f7-44b6-ada8-de08a609cd4d" />



## Task B

### Portscan
I installed nmap by using "sudo apt-get -y install nmap" 
I ran the portscan on the localhost using "sudo nmap -A localhost"
The scan lasted 8.23 seconds as only 1 port was open. 
As I scanned a domain name instead of an ip address it shows me the ip address of that domain *In the case of localhost it is always 127.0.0.1*
It skips all the closed ports and only shows the open ones it found
It shows me that port was 631 open, which is used for network printing.
It detected the OS and Version that this VM uses.
As it only checked the localhost of the VM there were no hops through a network

## Task C

I installed openSSH using "sudo apt-get -y install openssh" 
I scanned again using "sudo nmap -A localhost"
The scan was was still fast but this time 2 ports were open
Because I installed and started openSSH, port 22 is now open. The name of the service is SSH and the Version is OpenSSH 10.0p2 

## Task D

## Over the Wire Bandit (https://overthewire.org/)

Bandit 0 - Logged in using "ssh -p 2220 bandit0@bandit.lab.overthewire.org
Bandit 0 - 1 retrieved the password from the readme file by first using "ls" to see the file and then cat ./readme to see the content of the file
Bandit 1 - 2 retrieved the password from file called "-" by using "./-" 
Bandit 2 - 3 retrieved the password from file called "--spaces in this filename--" by using "cat './--spaces in this filename--'"
Bandit 3 - 4 retrieved the password from a hidden file by using "ls" to find the folder "inhere", changing the directory with "cd ./inhere", then using "ls -a" to see all files and then reading the hidden file with the "cat" command
Bandit 4 - 5 retrieved the password from a group of files by determining the filetype of all files using "file ./inhere/-file*". Read the file "-file07" which was the only one containing ASCII-text.
Bandit 5 - 6 retrieved the password from a large amount of files by looking for the only readable file containing 1033 bytes of data using "find . -size 1033c". Read the file using "cat" command











