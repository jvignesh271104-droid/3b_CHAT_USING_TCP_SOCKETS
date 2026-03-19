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
1. server.py
```
import socket

# Create socket
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Bind
host = '127.0.0.1'
port = 12345
server_socket.bind((host, port))

# Listen
server_socket.listen(1)
print("Server waiting for connection...")

# Accept connection
conn, addr = server_socket.accept()
print("Connected to:", addr)

while True:
    # Receive message from client
    client_msg = conn.recv(1024).decode()
    
    if client_msg.lower() == 'exit':
        print("Client disconnected")
        break
    
    print("Client:", client_msg)
    
    # Send reply to client
    msg = input("Server: ")
    conn.send(msg.encode())
    
    if msg.lower() == 'exit':
        break

# Close connection
conn.close()
server_socket.close()
```
2. client.py
```
import socket

# Create socket
client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Connect to server
host = '127.0.0.1'
port = 12345
client_socket.connect((host, port))

while True:
    # Send message to server
    msg = input("Client: ")
    client_socket.send(msg.encode())
    
    if msg.lower() == 'exit':
        break
    
    # Receive reply from server
    server_msg = client_socket.recv(1024).decode()
    print("Server:", server_msg)
    
    if server_msg.lower() == 'exit':
        break

# Close connection
client_socket.close()
```
## OUPUT
<img width="1034" height="172" alt="image" src="https://github.com/user-attachments/assets/a4ea8f58-96b6-415e-bbaf-cb21acfa384e" />

<img width="1016" height="131" alt="image" src="https://github.com/user-attachments/assets/6d4d2052-4454-4a20-b9db-6d96692ff14f" />


## RESULT
Thus, the python program for creating Chat using TCP Sockets Links was successfully 
created and executed.
