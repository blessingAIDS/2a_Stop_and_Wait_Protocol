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
***server***
```
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(1)
print("Server is listening on port 8000...")

c, addr = s.accept()
print(f"Connection established with {addr}")

while True:
    i = input("Enter data to send: ")
    if not i:
        break
    c.send(i.encode())

    ack = c.recv(1024).decode()
    if ack:
        print("Client:", ack)
    else:
        print("No acknowledgement received. Closing connection.")
        c.close()
        break
```

***client***

```
import socket

s = socket.socket()
s.connect(('localhost', 8000))
print("Connected to server.")

while True:
    data = s.recv(1024).decode()
    if not data:
        break
    print("Server:", data)
    s.send("Acknowledgement Received".encode())
```

## OUTPUT
***server***
<img width="1060" height="360" alt="image" src="https://github.com/user-attachments/assets/95958c6f-fa17-41b5-a3f6-28d811b801df" />

***client***

<img width="1058" height="214" alt="image" src="https://github.com/user-attachments/assets/d9175a9e-43a7-439f-8b08-ba3fa9d8b456" />


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
