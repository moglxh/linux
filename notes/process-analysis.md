# Process Analysis

## Objective

Understand parent processes, child processes, and process hierarchies.

## Parent Process

Command:

```bash
ps -ef | grep ssh
```

Output:

```text
root       75615       1  0 04:44 ?        00:00:00 sshd: /usr/sbin/sshd -D [listener] 0 of 10-100 startups
mog        76252       1  0 04:49 ?        00:00:00 /usr/bin/ssh-agent -s
mog       202654  109952  0 09:10 pts/0    00:00:00 grep --color=auto ssh
```

Observation:

The parent process starts and manages child processes.

## Child Process

Command:

```bash
pstree -p | grep ssh
```

Output:

```text
 pstree -p | grep ssh
           |-ssh-agent(76252)
           |-sshd(75615)
```

Observation:

Child processes are created by a parent process to perform specific tasks.

## Why Multiple SSH Processes?

Observation:

The main SSH service process listens for incoming connections. When a client connects, additional child processes may be created to handle authentication and user sessions.

## Observations

1. Every process has a parent process ID (PPID).
2. Processes can create child processes.
3. Process relationships form a tree structure.
4. systemd is ultimately the ancestor of most user-space processes.
5. Network services often create child processes to handle requests.

## Commands Used

```bash
ps -ef
ps -ef | grep ssh
pstree -p
```
