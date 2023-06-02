# EX-4 IMPLEMENTATION OF ADDRESS RESOLUTION PROTOCOL (ARP)

## DATE : 27-03-2023

## AIM:
To write a python program for simulating ARP protocols using TCP.

## ALGORITHM:
### Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.


### Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.


## PROGRAM:
### CLIENT:
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
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
### SERVER:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
 ip=input("Enter logical Address : ")
 s.send(ip.encode())
 print("MAC Address",s.recv(1024).decode())
 ```
## OUTPUT:

### CLIENT:
![241275691-3dbb4daf-1647-44e6-bb0c-b74f5a222670](https://github.com/Mena-Rossini/EX-4/assets/102855266/aa69a78e-d718-4bfc-8e7e-5120fa77feb1)

### SERVER:
![241275706-6d02353c-df7a-44b2-8248-6939b47e291d](https://github.com/Mena-Rossini/EX-4/assets/102855266/71094095-6f6e-4ffe-9a51-6a7958c5dad9)


## RESULT:
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
