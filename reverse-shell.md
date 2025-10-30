Auiannce Euwing
# Part 1: Installing a PHP web shell
- The PHP checks $_REQUEST["command"] and passes it to system(). So if you go to the PHP file and give command=whoami, the server runs whoami, and the command's output is sent back in the HTTP response.
- The <pre> tag is an HTML element. When you wrap command output in <pre>, newlines and multiple spaces from system() are shown exactly as they were produced, which makes command output readable. If you leave it out, then whitespace and newlines are collapsed, and formatting is lost.

# Part 2: Looking Around
- The danger website is located in the uploaded directory, which you can get to by doing  /var/www/danger.jeffondich.com
- wcisloa, vlahosstenn, sigmondm, sharnoffk, saidb, parsonj, jondich1, john-hurtubise1, hsolomon_webshell, and dennisd2. I know this is the usernames because we all followed the same naming system of our files.
- I don't have access to it, because it saying site not reached when I read the http://danger.jeffondich.com/uploadedimages/euwinga-webshell.php?command=ls%20-l%20/etc/passwd command
- I don't have access to this file. /etc/shadow contains one line per user, storing encrypted, hashed passwords and password policy information.
- You can find secret files by using the ls+-la command. I found  .(current directory), ..(parent directory), and jondich1.php (backup file) on the web page. 

# Part 4: launching a reverse shell
- The IP address of my Kali VM is 192.168.64.2 and I found it by running hostname -I in the terminal.
- The IP address of my host OS is 137.22.90.54 and I found it by running  curl -s ifconfig.me
- I do have a shell now and it is letting me execute commands on Kali. I know it is Kali because when I do hostname my kali information show up
- what do the % means:
   - %20 = space
   - %22 = "
   - %3E = >
   - %26 = &
   - %2F = /
- Description
   - The attacker starts a TCP listener on a chosen port
   - The Kali webserver hosts a webshell that accepts a command parameter via HTTP. When the specially-crafted URL is requested, the webshell runs a command which uses bash to open an outbound TCP connection to the attacker and redirects bash’s stdin/stdout/stderr to that TCP socket.
   - The attacker’s nc receives an interactive shell session. Commands typed into the nc listener are executed by the bash process on Kali, and the results are sent back over that TCP connection.
     
  
