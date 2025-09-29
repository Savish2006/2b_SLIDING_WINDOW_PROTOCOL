# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM:
Client:
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send : "))
l=list(range(size))
s=int(input("Enter Window Size : "))
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

Server:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement recived from the server".encode())
```

## OUPUT
Client:


<img width="473" height="253" alt="image" src="https://github.com/user-attachments/assets/dd3f24b7-55a2-4616-abb6-e0b20aefd249" />



Server:


<img width="497" height="245" alt="image" src="https://github.com/user-attachments/assets/4d599e21-6e52-4532-92cd-63525c7c75a1" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
