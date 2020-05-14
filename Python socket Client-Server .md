
#server.py

import socket

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.bind((socket.gethostname(), 1024))
s.listen(5)

while True:
    clientsocket, address = s.accept()
    print(f"Connection from {address} has been established")
    clientsocket.send(bytes("Welcome to the server", "utf-8"))
    
#client.py

import socket

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect((socket.gethostname(), 1024))

msg = s.recv(1024)
print(msg.decode("utf-8"))

    
