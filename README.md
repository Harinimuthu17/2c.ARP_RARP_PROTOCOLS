## SHREE LEKHA.S 212223110052
# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP/RARP protocols using TCP.
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
### client:
```
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
c, addr = s.accept()

address = {"165.165.80.80": "6A:08:AA:C2", "165.165.79.1": "8A:BC:E3:FA"}

while True:
    ip = c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())

c.close()
```
### server:
```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    ip = input("Enter logical Address: ")
    s.send(ip.encode())
    print("MAC Address", s.recv(1024).decode())
```
### PROGRAM:
![Screenshot 2024-03-10 193423](https://github.com/SHREELEKHAS/2c.ARP_RARP_PROTOCOLS/assets/149768910/ffde1142-7c53-4d4b-a4d9-a466ac893d2c)
![Screenshot 2024-03-10 193442](https://github.com/SHREELEKHAS/2c.ARP_RARP_PROTOCOLS/assets/149768910/c0adab05-511b-4bbc-9d5a-73ca803f1802)

## OUPUT - ARP
![Screenshot 2024-03-10 193544](https://github.com/SHREELEKHAS/2c.ARP_RARP_PROTOCOLS/assets/149768910/fac26237-e2c9-4015-8521-421f820f1572)

## PROGRAM - RARP
### client:
```
import socket

s = socket.socket()
s.bind(('localhost', 9000))
s.listen(5)
c, addr = s.accept()

address = {"6A:08:AA:C2": "192.168.1.100", "8A:BC:E3:FA": "192.168.1.99"}

while True:
    mac_address = c.recv(1024).decode()
    try:
        c.send(address[mac_address].encode())
    except KeyError:
        c.send("Not Found".encode()) 
```
### server:
```
import socket

s = socket.socket()
s.connect(('localhost', 9000))

while True:
    mac_address = input("Enter MAC Address: ")
    s.send(mac_address.encode())
    print("Logical Address:", s.recv(1024).decode())
```

### PROGRAM:
![Screenshot 2024-03-10 194336](https://github.com/SHREELEKHAS/2c.ARP_RARP_PROTOCOLS/assets/149768910/b0db037a-ec1c-443d-83f4-2a93853ca4db)
![Screenshot 2024-03-10 194348](https://github.com/SHREELEKHAS/2c.ARP_RARP_PROTOCOLS/assets/149768910/e671e9c9-1f40-4e97-9bc5-8d64b7915e82)

## OUPUT -RARP
![Screenshot 2024-03-10 194453](https://github.com/SHREELEKHAS/2c.ARP_RARP_PROTOCOLS/assets/149768910/65fd00c1-913a-4b64-86b9-b4fd80aff348)

## RESULT
Thus, the python program for simulating ARP/RARP protocols using TCP was successfully 
executed.
