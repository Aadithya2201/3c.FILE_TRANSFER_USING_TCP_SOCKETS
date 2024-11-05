# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS

# NAME: AADITHYA R
# REGISTER NO: 212223240001

## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
### CLIENT:
~~~
import socket
s = socket.socket()
host = socket.gethostname()
port = 60000
s.connect((host, port))
s.send("Hello server!".encode())
with open('received_file', 'wb') as f:
    print('receiving data...')
    while True:
        data = s.recv(1024)
        print('data=%s', (data))
        if not data:
            break
        f.write(data)
print('Successfully received the file')
s.close()
print('connection closed')
~~~
### SERVER:
~~~
import socket
port = 60000
s = socket.socket()
host = socket.gethostname()
s.bind((host, port))
s.listen(5)
print("Server listening on port", port)
while True:
    conn, addr = s.accept()
    print("Connected to", addr)
    data = conn.recv(1024)
    print('Server received', repr(data))
    filename = "C:\\Users\\admin\\Documents\\Computer Networks\\Ex3c\\mytext.txt"
    with open(filename, 'rb') as f:
        l = f.read(1024)
        while l:
            conn.send(l)
            print('Sent', repr(l))
            l = f.read(1024)
    print('Done sending')
    conn.send('Thank you for connecting'.encode())
    conn.close()
~~~
## OUPUT
### CLIENT :
![image](https://github.com/user-attachments/assets/959f143b-e233-498d-9214-367ea74a2ed5)
### SERVER :
![image](https://github.com/Rajaraman77/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/150319383/c88fed71-f545-499b-91fb-763c216f9cfb)

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
