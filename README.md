# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS

## Developed By : DHARAN ADITYA 
## Register No  : 212223040035

## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM:
## client.py
```
import socket
s = socket.socket()
host = socket.gethostname()
port = 60000
s.connect((host, port))
s.send("Hello server!".encode())
with open('received_file', 'wb') as f:
    while True:
        print('receiving data...')
        data = s.recv(1024)
        print('data=%s', (data))
        if not data:
            break
        f.write(data)
        f.close()
print('Successfully got the file')
s.close()
print('Connection closed')
```

## server.py
```
import socket
port = 60000
s = socket.socket()
host = socket.gethostname()
s.bind((host, port))
s.listen(5)
while True:
    conn, addr = s.accept()
    data = conn.recv(1024)
    print('Server received', repr(data))
    filename = 'F:\Comp_net\Ex no 7\sample.txt'
    with open(filename, 'rb') as f:
        while True:
            l = f.read(1024)
            if not l:
                break
            conn.send(l)
            print('Sent ', repr(l))
    print('Done sending')
    conn.send('Thank you for connecting'.encode())
    conn.close()
```
## OUTPUT:
## client:
![321575286-7e933ba3-9ef1-48d9-807d-0329b51e5c95](https://github.com/DharanAditya/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/147473834/278684d2-0e19-42fc-a663-1c604840bf6b)

## server.py:
![321575365-2f0d3016-ce39-44da-9ed5-3627d5bc7530](https://github.com/DharanAditya/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/147473834/9ab0f6d4-1b96-4abf-a94e-e2248decf639)

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
