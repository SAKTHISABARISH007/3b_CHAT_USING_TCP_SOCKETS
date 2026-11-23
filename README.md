# 3b.CREATION FOR CHAT USING TCP SOCKETS
## AIM
To write a python program for creating Chat using TCP Sockets Links.
## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server
4. Send and receive the message using the send function in socket.
## PROGRAM
server:
```
import socket

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

s.bind(('localhost', 8000))
s.listen(1)

print("Server waiting for connection...")

c, addr = s.accept()

print("Client connected:", addr)

while True:
    msg = c.recv(1024).decode()

    if msg.lower() == "exit":
        print("Client disconnected")
        break

    print("Client:", msg)

    reply = input("Server: ")
    c.send(reply.encode())

    if reply.lower() == "exit":
        break

c.close()
s.close()
```
client:
```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    msg = input("Client: ")
    s.send(msg.encode())

    if msg.lower() == "exit":
        break

    reply = s.recv(1024).decode()
    print("Server:", reply)

    if reply.lower() == "exit":
        break

s.close()
```
## OUPUT
<img width="1920" height="1080" alt="Screenshot 2026-11-23 085819" src="https://github.com/user-attachments/assets/0ff9dde6-3dc7-4dac-b430-4688f627b2d6" />

## RESULT
Thus, the python program for creating Chat using TCP Sockets Links was successfully 
created and executed.
