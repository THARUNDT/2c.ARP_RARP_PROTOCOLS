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

## PROGRAM - ARP
Client.py
```
import socket 
s=socket.socket() 
s.bind(('localhost',8080)) 
s.listen(5) 
c,addr=s.accept() 
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"}; 
while True:
    ip=c.recv(1024).decode() 
    try:
        c.send(address[ip].encode()) 
    except KeyError: 
        c.send("Not Found".encode())   

```
Server.py
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
![Screenshot 2025-04-19 142439](https://github.com/user-attachments/assets/c5d8d25f-7e57-40a7-bfdb-94713cd2b40d)

## PROGRAM - RARP
Client.py
```
import socket 
s=socket.socket() 
s.bind(('localhost',8080)) 
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

Server.py
```
import socket 
s=socket.socket() 
s.connect(('localhost',8080)) 
while True: 
    ip=input("Enter MAC Address : ")
    s.send(ip.encode()) 
    print("Logical Address",s.recv(1024).decode()) 

```
## OUPUT -RARP
![Screenshot 2025-04-19 143559](https://github.com/user-attachments/assets/c5286b24-bbf6-4df2-8c4b-7756dcf1f4d1)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
