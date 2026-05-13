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
# client
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"}; while True:
ip=c.recv(1024).decode()
try:
c.send(address[ip].encode())
except KeyError:
c.send("Not Found".encode())
```
# server
```
import socket
s = socket.socket()
s.connect(('localhost',8000))
while True:
ip = input("Enter logical address: ")
s.send(ip.encode())
print("MAC Address",s.recv(1024).decode())
```
## OUPUT - ARP

<img width="1211" height="185" alt="Screenshot 2026-05-13 201728 - Copy" src="https://github.com/user-attachments/assets/8a994077-6177-4151-84a0-b8887386289a" />
<img width="821" height="268" alt="Screenshot 2026-05-13 201748" src="https://github.com/user-attachments/assets/add500a5-bf33-44f3-bc74-f9130f6bf744" />



## PROGRAM - RARP
# client
```
import socket
s = socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr = s.accept()
address = {"6A:08:AA:C2":"165.165.80.1","8A:BC:E3:FA":"165.165.79.1"}
while True:
ip = c.recv(1024).decode()
try:
c.send(address[ip].encode())
except KeyError:
c.send("Not Found".encode())
```
# server
```
import socket
s = socket.socket()
s.connect(('localhost',8000))
while True:
ip = input("Enter MAC address: ")
s.send(ip.encode())
print("Logical Address",s.recv(1024).decode())
```
## OUPUT -RARP

<img width="1209" height="221" alt="Screenshot 2026-05-13 202442" src="https://github.com/user-attachments/assets/64804ce1-1807-4f9a-94a4-09fc41c4a3f5" />
<img width="1211" height="268" alt="Screenshot 2026-05-13 202458" src="https://github.com/user-attachments/assets/1aed769b-3526-4105-b05b-26c3cff87292" />


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
