# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.
P
## PROGRAM - ARP
client
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"255.255.255.0":"02:01:39:D4:C0:7E","10.82.64.78":"8A:BC:E3:FA"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())

```
server
```
import socket 
s=socket.socket() 
s.connect(('localhost',8000)) 
while True: 
    ip=input("Enter logical Address : ") 
    s.send(ip.encode()) 
    print("MAC Address",s.recv(1024).decode())

```
## OUPUT - ARP
<img width="608" height="206" alt="image" src="https://github.com/user-attachments/assets/f301739d-cfde-4653-97fb-d647dd33689b" />


<img width="397" height="125" alt="Screenshot 2025-09-15 112905" src="https://github.com/user-attachments/assets/cb0a8c46-c3d9-441e-b47d-0a547fffccd0" />


<img width="676" height="134" alt="image" src="https://github.com/user-attachments/assets/07a5e44a-87aa-4f97-afb4-a2b796b96888" />

## PROGRAM - RARP
client.py 
```
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"};
while True:
 ip=c.recv(1024).decode()
 try:
   c.send(address[ip].encode())
 except KeyError:
   c.send("Not Found".encode())
```
server.py
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
 ip=input("Enter MAC Address : ")
 s.send(ip.encode())
 print("Logical Address",s.recv(1024).decode())
```
## OUPUT -RARP
![image](https://github.com/user-attachments/assets/c73a38b5-8af5-40f3-a1f5-9c891dbf715f)

![image](https://github.com/user-attachments/assets/6ff2cb78-df9b-423f-bf9d-f42df9c0dbf5)


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
