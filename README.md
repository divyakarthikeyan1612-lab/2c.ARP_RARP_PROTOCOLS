# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## ARP

1. Start the program.
2. Create a server socket and bind it to port 8000.
3. Accept the client connection.
4. Get the IP address from the client.
5. Find the corresponding MAC address.
6. Send the MAC address to the client.
7. Stop the program.

## RARP

1. Start the program.
2. Create a server socket and bind it to port 9000.
3. Accept the client connection.
4. Get the MAC address from the client.
5. Find the corresponding IP address.
6. Send the IP address to the client.
7. Stop the program.
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
1)Server
```
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)

c, addr = s.accept()

address = {
    "165.165.80.80": "6A:08:AA:C2",
    "165.165.79.1": "8A:BC:E3:FA"
}

while True:
    ip = c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```
2)Client 
```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    ip = input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address", s.recv(1024).decode())
```
## OUTPUT - ARP
<img width="1906" height="981" alt="image" src="https://github.com/user-attachments/assets/9a553dba-b6f2-4145-bfa4-1906fd75aa55" />

## PROGRAM - RARP
1)Server 
```
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
```
2)Client
```
import socket

s = socket.socket()
s.connect(('localhost', 9000))

while True:
    ip = input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address", s.recv(1024).decode())
```
## OUTPUT -RARP
<img width="1905" height="983" alt="image" src="https://github.com/user-attachments/assets/b6f51220-1bbe-43c0-8c07-66fc1ff5c1e6" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
