# 2a_Stop_and_Wait_Protocol
## AIM 
To write a python program to perform stop and wait protocol
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
```
Server.py
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
    print("Frame received:", data)
    conn.send("ACK".encode())
conn.close()

Client.py
import socket
s = socket.socket()
s.connect(('localhost', 8000))
n = int(input("Enter number of frames: "))
for i in range(n):
    msg = input("Enter frame: ")
    s.send(msg.encode())
    ack = s.recv(1024).decode()
    print("Received:", ack)
s.close()
```
## OUTPUT

<img width="775" height="186" alt="image" src="https://github.com/user-attachments/assets/b81a6f0f-748c-4625-b197-31277a4f2577" />

<img width="789" height="202" alt="image" src="https://github.com/user-attachments/assets/2fbcf103-1ba5-4817-8c8e-b7a9c0f7af28" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
