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

CLIENT
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
SERVER
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
CLIENT


![Screenshot 2024-10-01 085533](https://github.com/user-attachments/assets/cca6a3cf-22be-45b8-bc72-e372242e3b12)

SERVER

![Screenshot 2024-10-01 085523](https://github.com/user-attachments/assets/e1b0dce3-773e-436c-8e0b-21d42eba3bab)


## PROGRAM - RARP

CLIENT
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
SERVER

```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
    ip=input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address",s.recv(1024).decode())


```
## OUPUT -RARP

CLIENT

![Screenshot 2024-10-01 092430](https://github.com/user-attachments/assets/f3657822-1c9e-4a68-9c06-051264707993)

SERVER

![Screenshot 2024-10-01 092440](https://github.com/user-attachments/assets/629b2d1e-1362-4feb-a582-c6332dafb03d)


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
