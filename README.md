# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## NAME: TAMIZHAN B
## REF NO: 212225230283
### PROGRAM:
ARP:
## Server:
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
## CLIENT:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
OUPUT - ARP
```
## PROGRAM-RARP:
## Server
import socket

s = socket.socket()
s.bind(('localhost', 9000))
s.listen(5)

c, addr = s.accept()

address = {
    "6A:08:AA:C2": "192.168.1.100",
    "8A:BC:E3:FA": "192.168.1.99"
}

while True:
    ip = c.recv(1024).decode()

    try:
        c.send(address[ip].encode())

    except KeyError:
        c.send("Not Found".encode())
## Cilent
import socket

s = socket.socket()
s.connect(('localhost', 9000))

while True:
    ip = input("Enter MAC Address : ")
    
    s.send(ip.encode())
    
    print("Logical Address", s.recv(1024).decode())
OUPUT -RARP
## OUPUT -RARP
<img width="1600" height="820" alt="image" src="https://github.com/user-attachments/assets/1bef07fb-3752-4329-84ef-f9e82f27028a" />
<img width="1600" height="823" alt="image" src="https://github.com/user-attachments/assets/99abe713-b0d3-4e13-877f-5e9f3dad1cf3" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
