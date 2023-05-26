# IMPLEMENTATION OF REVERSE ADDRESS RESOLUTION PROTOCOL(RARP)
# EXP: 5
# DATE:05-04-2023
# AIM:
To write a python program for implementing Reverse Address Resolution Protocol(RARP).

# ALGORITHM:
## Client:
Start the program

Using datagram sockets UDP function is established.

Get the MAC address to be converted into IP address.

Send this MAC address to server.

Server returns the IP address to client.
## Server:

Start the program.

Server maintains the table in which IP and corresponding MAC addresses are stored.

Read the MAC address which is send by the client.

Map the IP address with its MAC address and return the IP address to client.

# PROGRAM:

## CLIENT:

```
import socket
s = socket.socket()
s.bind(("localhost", 8000))
s.listen(5)
c, addr = s.accept()
address={"6A:08:AA:C2":"165.165.80.80","8A:BC:E3:FA":"165.165.79.1"};
while True:
   ip=c.recv(1024).decode()
   try:
       c.send(address[ip].encode())
   except KeyError:
       c.send("Not found".encode())
 ```
## SERVER:

```
import socket
s=socket.socket()
s.connect(("localhost", 8000))
while True:
    ip=input("Enter the MAC address:")
     
    s.send(ip.encode())
    print("logical Address",s.recv(1024).decode())
```
CLIENT OUTPUT :

![image](https://github.com/DhanushPalani/EX-NO-5/assets/121594640/22589376-c87d-4ef2-a52d-ac30f96fa164)

SERVER OUTPUT :

![image](https://github.com/DhanushPalani/EX-NO-5/assets/121594640/5c9e969b-742f-4ccc-8f7d-0637347c2874)

RESULT:

Thus, the python program for simulating RARP protocols using TCP was successfully executed.
