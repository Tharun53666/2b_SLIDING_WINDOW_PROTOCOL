# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
# REG NO: 212224240170
#
## AIM:
 To write a python program for implementation of sliding window protocol
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM:
## client:
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames:"))
l=list(range(size))
s=int(input("Enter window size:"))
st=0
i=0
while True:
    while(i<len(l)):
        st+=s
        c.send(str(l[i:st]).encode())
        ack=c.recv(1024).decode()
        if ack:
            print(ack)
            i+=s
```
## server:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknoledgement recieved from the server".encode())
```
## OUTPUT:
## client:
![Screenshot 2025-04-12 113832](https://github.com/user-attachments/assets/a1359b0d-f4c6-40ad-8451-5524f0c3b1ad)



## server:

![Screenshot 2025-04-12 113858](https://github.com/user-attachments/assets/0689791a-8629-46c9-886c-f25c924f5ed0)



## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
