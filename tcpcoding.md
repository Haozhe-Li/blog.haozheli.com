# Coding with TCP Sockets Notes

## 1. Address and Port

- **IP Address**:
  - Identifies a computer.
  - Assigned by Internet Service Provider using DHCP.

- **TCP Port**:
  - Identifies a connection in a process.
  - Should use unassigned or ephemeral port numbers (49152–65535) unless necessary.

- **TCP/IP Socket**:
  - Bi-directional communication channel.
  - Each end has an IP address and TCP port number.

## 2. Client-Server Sockets

- **Server Design**:
  - Opens a socket to listen for connection attempts (S1).
  - Accepts connection attempts and opens a new socket for communication (S2).

- **Client Design**:
  - Opens a socket and connects to the server's listening socket (C1).
  
- **Communication**:
  - Both server and client read/write data to their connection socket.
  - Use `recv` and `send` functions for communication.
  - Avoid using very large buffers for efficiency.

## C Code Examples:

### Server
```c
// Includes and variable declarations...

int listener = socket(AF_INET, SOCK_STREAM, 0);
bind(listener, (void *)&ipOfServer , sizeof(ipOfServer));
listen(listener, 20);

while(1) {
  int connection = accept(listener, NULL, NULL);
  // Communication and closing connection...
}

close(listener);
```

### Client
```c
// Includes and variable declarations...

int connection = socket(AF_INET, SOCK_STREAM, 0);
connect(connection, (void *)&ipOfServer, sizeof(struct sockaddr_in));
// Communication and closing connection...
```

## Python Code Examples:

### Server
```python
# Import and variable declarations...

with socket(AF_INET, SOCK_STREAM) as listener:
  listener.bind(('', s1port))
  listener.listen(20);

  while True:
    connection, addr = listener.accept()
    # Communication and closing connection...
```

### Client
```python
# Import and variable declarations...

with socket(AF_INET, SOCK_STREAM) as connection:
  connection.connect((serverIP, s1port))
  # Communication (automatically closed by 'with' block)...
```
