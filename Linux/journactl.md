# Journactl

## Introduction

`journactl` is a utility for querying and interacting with the journalctl logs on Linux systems. It is part of the `systemd` suite of tools.

## Configuration

Can be configured via the `/etc/systemd/journald.conf` file.

```bash
sudo vim /etc/systemd/journald.conf
```

## Options

Give some common options.

### -r, --reverse

Show the newest entries first.

```bash
journactl -r
```

### -u, --unit

Show logs for a specific unit (service).

```bash
journactl -u nginx
```

### --list-boots

List all boots.
- `BOOT_ID` is the boot ID.
  - `0` is the current boot.
  - `1` is the previous boot.
  - `2` is the boot before that.
 

```bash
journactl --list-boots
```

### -b, --boot

Show logs for a specific boot.

```bash
journactl -b 1  # Show logs for the previous boot.
```

### -p, --priority

Show logs with a specific priority level.
- `0` is `emerg`.
- `1` is `alert`.
- `2` is `crit`.
- `3` is `err`.
- `4` is `warning`.
- `5` is `notice`.
- `6` is `info`.
- `7` is `debug`.

```bash
journactl -p 3  # Show logs with priority level `err`.
```

### -k, --dmesg

Show only kernel messages.

```bash
journactl -k
```

### -s, --since

Show logs since a specific time.

```bash
journactl -s "2021-01-01 00:00:00"
```
