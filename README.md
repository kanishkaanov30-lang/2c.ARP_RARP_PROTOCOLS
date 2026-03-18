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
~~~
Server Program (server.py) 
import socket 
s = socket.socket() 
s.bind(('localhost', 8000)) 
s.listen(1) 
print("Waiting for connection...") 
conn, addr = s.accept() 
print("Connected to", addr) 
while True: 
data = conn.recv(1024).decode() 
if not data: 
break 
print("Frames received:", data) 
ack = "ACK for " + data 
conn.send(ack.encode()) 
conn.close()
~~~
## OUPUT - ARP
![WhatsApp Image 2026-03-18 at 10 39 32 AM](https://github.com/user-attachments/assets/2303238c-6c9a-4ea8-b1f8-9e3eb65478bf)

## PROGRAM - RARP
~~~
import socket 
s = socket.socket() 
s.connect(('localhost', 8000)) 
n = int(input("Enter number of frames: ")) 
w = int(input("Enter window size: ")) 
frames = list(range(1, n+1)) 
i = 0 
while i < n: 
send_frames = frames[i:i+w] 
msg = " ".join(map(str, send_frames)) 
print("Sending frames:", msg) 
s.send(msg.encode()) 
ack = s.recv(1024).decode() 
print("Received:", ack) 
i += w 
s.close()
~~~
## OUPUT -RARP
![WhatsApp Image 2026-03-18 at 10 39 40 AM](https://github.com/user-attachments/assets/a2b4fa66-85fd-45d1-972e-bfe56722d0e1)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
