# 4.Execution_of_NetworkCommands
## AIM :Use of Network commands in Real Time environment
## Software : Command Prompt And Network Protocol Analyzer
## Procedure: To do this EXPERIMENT- follows these steps:
<BR>
In this EXPERIMENT- students have to understand basic networking commands e.g cpdump, netstat, ifconfig, nslookup ,traceroute and also Capture ping and traceroute PDUs using a network protocol analyzer 
<BR>
All commands related to Network configuration which includes how to switch to privilege mode
<BR>
and normal mode and how to configure router interface and how to save this configuration to
<BR>
flash memory or permanent memory.
<BR>
This commands includes
<BR>
• Configuring the Router commands
<BR>
• General Commands to configure network
<BR>
• Privileged Mode commands of a router 
<BR>
• Router Processes & Statistics
<BR>
• IP Commands
<BR>
• Other IP Commands e.g. show ip route etc.
<BR>

##PROGRAM:
Client:
```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    ip = input("Enter the website you want to ping (or type 'exit' to quit): ")
    s.send(ip.encode('utf-8'))
    if ip.lower() == 'exit':
        break
    print(s.recv(4096).decode('utf-8'))

s.close()
```
Server:
```
import socket
from pythonping import ping

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
print("Server listening on port 8000...")
c, addr = s.accept()
print(f"Connection from {addr}")

while True:
    try:
        hostname = c.recv(1024).decode('utf-8')
        if not hostname or hostname.lower() == 'exit':
            print("Client disconnected.")
            break
        response = ping(hostname, verbose=False, count=4)
        c.send(str(response).encode('utf-8'))
    except Exception as e:
        c.send(f"Ping failed: {e}".encode('utf-8'))

c.close()
```

## Output
Client:

<img width="752" height="391" alt="image" src="https://github.com/user-attachments/assets/c5b2f9ee-6c26-4905-8d3c-9be5594fd389" />

Server:

<img width="783" height="156" alt="image" src="https://github.com/user-attachments/assets/9104d3cd-8bb0-4528-869b-76f210b1b6ca" />

Traceroute:

<img width="1105" height="520" alt="image" src="https://github.com/user-attachments/assets/e83f2846-1004-4658-a830-e535b13ff76d" />

IPCONFIG:

<img width="1242" height="840" alt="image" src="https://github.com/user-attachments/assets/24318884-730c-4b86-bcbd-1f03e6798a82" />

NSLOOKUP:

<img width="633" height="461" alt="image" src="https://github.com/user-attachments/assets/2fa01740-250f-48c5-ae8e-5fb2cdd6d579" />

NETSTAT:

<img width="1153" height="871" alt="image" src="https://github.com/user-attachments/assets/50c9ed23-b5d5-408e-b91b-524933e2272a" />

TCP DUMP:

<img width="1536" height="941" alt="image" src="https://github.com/user-attachments/assets/3c03e4c5-8ee2-4c46-9058-f421515fb32e" />


## Result
Thus Execution of Network commands Performed 
