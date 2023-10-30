# Client-Server Application with Serialization (Advanced)

The objective of this exercise is to understand how serialization is used in network communication to transmit data between different systems.
This is a challenging exercise that will introduce some advanced topics. Please, review the resources befor start coding and be sure you understand what you're doing.

## Requirements:

1. Create a client-server application in Python.
2. The client should send a Python dictionary to the server.
3. The server will serialize the dictionary, send it over a network connection, and then deserialize and process it.
4. Save your code in a file named `4-net.py`.

## Resources:

1. **Python Official Documentation**:
   - **Socket Programming**: The official Python documentation provides a comprehensive guide to using sockets. It's a great resource for understanding the basics and advanced concepts.
     [Python Sockets](https://docs.python.org/3/library/socket.html)

2. **Real Python Tutorials**:
   - **Socket Programming in Python (Guide)**: This is a beginner-friendly guide that covers the basics of how to use sockets in Python.
     [Real Python Socket Programming](https://realpython.com/python-sockets/)

3. **GeeksforGeeks Articles**:
   - **Socket Programming with Multi-threading in Python**: A guide that explains how to set up multi-threaded socket applications.
     [GeeksforGeeks Multi-threaded Socket Programming](https://www.geeksforgeeks.org/socket-programming-multi-threading-python/)
   - **Python Serialization**: A brief introduction to serialization in Python.
     [GeeksforGeeks Python Serialization](https://www.geeksforgeeks.org/serialization-in-python/)

4. **TutorialsPoint**:
   - **Python Network Programming**: TutorialsPoint provides a set of tutorials that deal with different aspects of network programming in Python, including socket programming.
     [TutorialsPoint Python Network Programming](https://www.tutorialspoint.com/python_network_programming/index.htm)

5. **YouTube**:
   - Various YouTube channels offer tutorials and walkthroughs on Python socket programming. A simple search for "Python socket programming tutorial" will yield numerous results. Some channels that regularly provide quality Python tutorials include **Corey Schafer**, **Tech With Tim**, and **sentdex**.

## Instructions:

**Server:**

1. Start by importing the necessary modules:
   ```python
   import socket
   import json
   ```

2. Create a function named `start_server` that sets up a server using the socket library.
   - Set up a server socket to listen for incoming connections on a specific port.
   - Upon receiving a connection, read the serialized data.
   - Deserialize the data using the `json` module.
   - Print the received dictionary.
   - Close the connection.

**Client:**

3. Create a function named `send_data` that acts as the client:
   - Establish a connection to the server.
   - Serialize a Python dictionary.
   - Send the serialized data to the server.
   - Close the connection.

4. Remember to handle exceptions for potential errors like connection failures.

5. Save your work in `4-net.py`.

### Testing Your Code:

```python
#!/usr/bin/env python3
import threading
import time

net_serialize = __import__('4-net')

def main():
    # Start the server in a separate thread
    server_thread = threading.Thread(target=net_serialize.start_server)
    server_thread.start()

    # Give server some time to start listening
    time.sleep(1)

    # Run the client to send data
    sample_dict = {
        'name': 'Alice',
        'age': 30,
        'city': 'Paris'
    }
    net_serialize.send_data(sample_dict)

    # Ensure server thread ends
    server_thread.join()

if __name__ == "__main__":
    main()
```

### Expected Output:

```
Received Dictionary from Client:
{'name': 'Alice', 'age': 30, 'city': 'Paris'}
```
