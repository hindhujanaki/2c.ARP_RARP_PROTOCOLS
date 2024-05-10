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
## Client:
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
 ## Server:
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
## Client
![image](https://github.com/hindhujanaki/2c.ARP_RARP_PROTOCOLS/assets/148514666/67bad3ae-d555-4e72-a9d4-5b96398418a5)
## Server
![image](https://github.com/hindhujanaki/2c.ARP_RARP_PROTOCOLS/assets/148514666/66121605-81d3-4d39-b2c7-a731bf5bcf56)

## PROGRAM - RARP
## Client
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
## Server
```
import socket s=socket.socket()
s.connect(('localhost',9000))
while True:
 ip=input("Enter MAC Address : ")
REG NO:
  s.send(ip.encode())
  print("Logical Address",s.recv(1024).decode())
```
## OUPUT -RARP
## Client
![image](https://github.com/hindhujanaki/2c.ARP_RARP_PROTOCOLS/assets/148514666/194c803c-0d94-4c12-99a5-4c6fbcfd5a62)

## Server
![image](https://github.com/hindhujanaki/2c.ARP_RARP_PROTOCOLS/assets/148514666/c4c06b3d-1b89-4d46-bb89-78db62095610)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
