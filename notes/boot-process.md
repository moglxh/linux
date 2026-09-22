# Boot Process

# Objective

Understand the Linux boot process and identify PID 1 and the default target.

## PID 1

Command:

```bash
ps -p 1
```

Output:ps -p 1
    PID TTY          TIME CMD
      1 ?        00:00:02 systemd


```text
<PASTE OUTPUT HERE>
```

Observation:

PID 1 is the first userspace process started by the kernel. On this system it is systemd.

## Default Target

Command:

```bash
systemctl get-default
```

Output:

```text
systemctl get-default
graphical.target
```

Observation:

The default target determines what state the system boots into.

## Observations

1.
2.
3.
4.
5.

## Commands Used

```bash
ps -p 1
systemctl get-default
systemctl list-units --type=target
systemd-analyze
