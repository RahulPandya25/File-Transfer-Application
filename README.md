# File-Transfer-Application

Course COMP–8567
Instructor Dr. B. Boufama
Project (Recorded chapter 08, its PDFs and its three examples are available online)
Due date Aug. 20, 2020, to be demonstrated to Mr. Xiaofeng Liu (liu1ew@uwindsor.ca)
Note: This project is to be done either by pairs (two students) or by a single student
Write two programs (in C), a client and a server, to implement a simple text file
transfer application. The server process and the client process will run on two different machines(
E.g., bravo and charlie) and the communication between the two processes is achieved
using sockets.
The server task can be summarized as follows :
 The server must start running before any client and wait for connections.
 When the server gets a client, forks and, let the child process take care of the client in a
separate function, called serviceClient. The parent process goes back to wait for the next
client.
 Then, the server’s child process gets in an infinite loop and :
– Reads a command from the client’s socket, the command can be one out of "get
fileName", "put fileName" or "quit".
– If the client sends "quit", then the server’s child, closes its socket and quits.
– If the client sends "get fileName", then (if file exists) the server’s child opens the file
and writes all its contents to the client’s socket. The client process saves it locally.
ASCII code 4 (CTR-D) can be sent by the server to signal end-of-file to the client.
– If the client sends "put fileName", then the server’s child reads all the file’s contents
from socket and saves it locally. ASCII code 4 (CTR-D) can be sent by the client to
signal end-of-file to the server.
Once the client process connects to the server, it
 gets into an infinite loops
1. reads a command from keyboard, "get fileName", "put fileName" or "quit"
2. writes the command to the server,
3. if command is "quit", the client process closes its socket and quits
4. otherwise, it performs file transfer and prints a message like: "file uploaded" or "file
downloaded".
