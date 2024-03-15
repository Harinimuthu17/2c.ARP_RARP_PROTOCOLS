## M.HARINI 212222240035
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
![image](https://github.com/Harinimuthu17/2c.ARP_RARP_PROTOCOLS/assets/130278614/f0ace5d6-3cb1-4dd6-a66e-c8dbead750a3)

![image](https://github.com/Harinimuthu17/2c.ARP_RARP_PROTOCOLS/assets/130278614/37f50960-837c-4f2b-afe1-bb1c3b1ba563)

## OUPUT - ARP:

![image](https://github.com/Harinimuthu17/2c.ARP_RARP_PROTOCOLS/assets/130278614/b523cfc2-7886-4732-a18d-3c2bb6830ad1)



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
![image](https://github.com/Harinimuthu17/2c.ARP_RARP_PROTOCOLS/assets/130278614/25d4f6c2-fd01-459f-a2d7-dfb5196ba6d9)

![image](https://github.com/Harinimuthu17/2c.ARP_RARP_PROTOCOLS/assets/130278614/7d642cde-90c3-47f8-91be-7c97a923c472)


## OUTPUT -RARP: 

![image](https://github.com/Harinimuthu17/2c.ARP_RARP_PROTOCOLS/assets/130278614/6b4c56cd-1adc-46c3-b37b-a9350e19f4ac)



## RESULT
Thus, the python program for simulating ARP/RARP protocols using TCP was successfully 
executed.
