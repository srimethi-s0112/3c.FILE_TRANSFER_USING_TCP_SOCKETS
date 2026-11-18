# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
## SERVER
```

import socket

# Create server socket
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

host = '127.0.0.1'
port = 5000

server_socket.bind((host, port))
server_socket.listen(1)

print("Server waiting for connection...")

client_socket, addr = server_socket.accept()
print("Connected to:", addr)

# Open and read file
file = open("sample.txt", "rb")
data = file.read()

# Send file to client
client_socket.sendall(data)

print("File sent successfully")

file.close()
client_socket.close()
server_socket.close()
```
## CLIENT
```
import socket

# Create client socket
client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

host = '127.0.0.1'
port = 5000

client_socket.connect((host, port))

print("Connected to server")

# Receive file from server
with open("received.txt", "wb") as file:
    while True:
        data = client_socket.recv(1024)

        if not data:
            break

        file.write(data)

print("File received successfully")

client_socket.close()
```
## OUTPUT
## SERVER

<img width="686" height="235" alt="image" src="https://github.com/user-attachments/assets/f18ef078-e18f-48a7-b7ab-578bfd8b2742" />


## CLIENT

<img width="577" height="178" alt="image" src="https://github.com/user-attachments/assets/85f3862e-159d-4958-bd3b-98a9c63581c4" />

## SAMPLE TXT

<img width="432" height="141" alt="image" src="https://github.com/user-attachments/assets/be48a3b6-9e2c-4cf5-beb1-9ad02b2d6b8d" />


## RECEIVED TXT

<img width="488" height="161" alt="image" src="https://github.com/user-attachments/assets/522c6fbc-baa9-400a-ae10-3382f7e3d632" />


## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
