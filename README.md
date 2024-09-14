# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
SERVER:
```import socket
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
CLIENT:
```import socket
s=socket.socket()
s.connect(('localhost',8000))
while True: 
 print(s.recv(1024).decode())
 s.send("acknowledgement recived from the server".encode())
```

## OUPUT

 SERVER:
 
 ![image](https://github.com/user-attachments/assets/4bb903c3-9504-4324-a669-f4d253fdbbf0)
 
 CLIENT:
 
 ![image](https://github.com/user-attachments/assets/bd87d3a7-8390-4f36-bde5-3d9a72498b38)

 

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
