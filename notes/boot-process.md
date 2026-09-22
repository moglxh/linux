# Boot Process

## Objective

Understand the Linux boot process, PID 1, and the default target.

## PID 1

Command:

```bash
ps -p 1
```

Output:

```text
PID TTY          TIME CMD
1   ?        00:00:02 systemd
```

Observation:

PID 1 is systemd on this Kali system.

## Default Target

Command:

```bash
systemctl get-default
```

Output:

```text
graphical.target
```

Observation:

The system boots into graphical mode by default.

## Observations

1. The kernel starts before any userspace process.
2. systemd is PID 1 on this machine.
3. systemd manages services and the boot process.
4. The default target is `graphical.target`.
5. Targets define the system state after boot.

## Commands Used

```bash
ps -p 1
systemctl get-default
systemctl list-units --type=target
systemd-analyze
```
