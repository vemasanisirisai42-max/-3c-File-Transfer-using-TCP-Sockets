# -3c-File-Transfer-using-TCP-Sockets
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
server
```

import socket

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.bind(('localhost', 8002))
s.listen(1)

print("Server waiting for connection...")
conn, addr = s.accept()
print("Client connected")

filename = input("Enter file name: ")

with open(filename, 'rb') as f:
    data = f.read()

conn.sendall(data)
print("File sent successfully")

conn.close()
s.close()
```
client
```
import socket

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect(('localhost', 8002))

with open('received_file.txt', 'wb') as f:
    while True:
        data = s.recv(1024)
        if not data:
            break
        f.write(data)

print("File received successfully")

s.close()

```
## OUPUT
## server

<img width="373" height="165" alt="image" src="https://github.com/user-attachments/assets/9b350b33-29ba-4ce8-960d-8a40727edd60" />

## client

<img width="382" height="147" alt="image" src="https://github.com/user-attachments/assets/b7570ac4-4bc9-4ed5-978f-a1c729f7ff80" />

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
