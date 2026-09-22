# Service Analysis

## Objective

Analyze a Linux service and identify its executable, PID, and logs.

## Service

```bash
systemctl status ssh
```

Service:

```text
ssh.service
```

## Executable

```bash
systemctl show ssh -p ExecStart
```

Output:

```text
ExecStart={ path=/usr/sbin/sshd ; argv[]=/usr/sbin/sshd -D $SSHD_OPTS ; ignore_errors=no ; start_time=[n/a] ; stop_time=[n/a] ; pid=0 ; code=(null) ; status=0/0 }
```

Observation:

This is the program systemd starts for the SSH service.

## PID

Command:

```bash
systemctl status ssh
```

Output:

```text
Main PID: 75615 (sshd)
```

Observation:

This is the running process associated with the service.

## Logs

Command:

```bash
journalctl -u ssh -n 10
```

Output:

```text
Sep 21 22:06:57 kali sshd[731]: Server listening on :: port 22.
Sep 21 22:06:57 kali systemd[1]: Started ssh.service - OpenBSD Secure Shell server.
Sep 22 01:09:46 kali systemd[1]: Stopping ssh.service - OpenBSD Secure Shell server...
Sep 22 01:09:46 kali sshd[731]: Received signal 15; terminating.
Sep 22 01:09:46 kali systemd[1]: ssh.service: Deactivated successfully.
Sep 22 01:09:46 kali systemd[1]: Stopped ssh.service - OpenBSD Secure Shell server.
Sep 22 01:14:26 kali systemd[1]: Starting ssh.service - OpenBSD Secure Shell server...
Sep 22 01:14:26 kali sshd[75615]: Server listening on 0.0.0.0 port 22.
Sep 22 01:14:26 kali sshd[75615]: Server listening on :: port 22.
Sep 22 01:14:26 kali systemd[1]: Started ssh.service - OpenBSD Secure Shell server.```

Observation:

The logs show recent activity related to the SSH service.

## Observations

1. Services are managed by systemd.
2. Each service starts one or more executables.
3. A running service usually has an associated PID.
4. systemctl shows service state and process information.
5. journalctl provides service-specific logs.

## Commands Used

```bash
systemctl status ssh
systemctl show ssh -p ExecStart
journalctl -u ssh -n 10
```
