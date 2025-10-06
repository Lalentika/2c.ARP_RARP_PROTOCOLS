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
Client-ARP:
```
import socket
s=socket.socket()
s.bind(('localhost',8080))
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

Server-ARP:
```
import socket
s=socket.socket()
s.connect(('localhost',8080))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
```

## OUPUT - ARP

<img width="675" height="289" alt="Screenshot 2025-10-06 112137" src="https://github.com/user-attachments/assets/bb23d119-37c0-46dd-bfe9-7fa2cfb7feb3" />

## PROGRAM - RARP
Server-RARP:
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
 ip=input("Enter MAC Address : ")
 s.send(ip.encode())
 print("Logical Address",s.recv(1024).decode())
```
Client-RARP:
```
import socket
s=socket.socket()
s.bind(('localhost',9000))
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

## OUPUT -RARP

<img width="694" height="285" alt="image" src="https://github.com/user-attachments/assets/91236350-1dc0-4a68-8b6f-0c410c6a8dca" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
