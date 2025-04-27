# ipmitool Cheat Sheet

`ipmitool` is a command-line utility for managing and configuring devices that support the Intelligent Platform Management Interface (IPMI). It is commonly used for server management tasks such as power control, user management, and hardware monitoring.

---

## Installation
```sh
sudo apt install ipmitool
```

---

## Basic Usage
```sh
ipmitool -I lanplus -H <BMC_IP> -U <user> -P <PWD> -C 17 <cmd>
```
- Replace `<BMC_IP>`, `<user>`, and `<PWD>` with your BMC IP, username, and password.
- `-C 17` specifies the cipher suite (optional, but often required).

---

## Common Commands

### Chassis & Power Control
- Get power status:
  ```sh
  ipmitool chassis power status
  ```
- Power control:
  ```sh
  ipmitool chassis power off
  ipmitool chassis power on
  ipmitool chassis power cycle
  ipmitool chassis power reset
  ```

### User Management
- List users:
  ```sh
  ipmitool user list
  ```
- Set username:
  ```sh
  ipmitool user set name <user_id> <name>
  ```
- Set password:
  ```sh
  ipmitool user set password <user_id> <password>
  ```
- Set privilege:
  ```sh
  ipmitool user priv <user_id> <channel_number> <privilege_level>
  ```

### Management Controller (MC)
- Show firmware version:
  ```sh
  ipmitool mc info
  ```
- Reset MC:
  ```sh
  ipmitool mc reset warm
  ipmitool mc reset cold
  ```

### FRU (Field Replaceable Unit)
- Print FRU info:
  ```sh
  ipmitool fru print
  ```

### Sensor & System Log
- List sensors:
  ```sh
  ipmitool sdr list
  ipmitool sensor list
  ```
- System Event Log (SEL):
  ```sh
  ipmitool sel info
  ipmitool sel list
  ipmitool sel elist  # Extended list
  ```

---

## Debug & Information
- Print LAN settings:
  ```sh
  ipmitool lan print
  ```
- Start ipmitool shell:
  ```sh
  ipmitool -H <ip> -U <user> shell
  # Type 'help' in the shell for more commands
  ```
- Show system event log:
  ```sh
  ipmitool -H <ip> -U <user> sel list
  ```
- List sensor data:
  ```sh
  ipmitool -H <ip> -U <user> sdr
  ```

---

## References
- https://confluence.nvidia.com/display/GM/Ipmitool+command+usage
- https://confluence.nvidia.com/pages/viewpage.action?pageId=2468685016
- https://confluence.nvidia.com/pages/viewpage.action?pageId=1301737891
- https://github.com/ipmitool/ipmitool
- https://github.com/openbmc/docs/blob/master/IPMITOOL-cheatsheet.md
- https://www.ibm.com/docs/zh-tw/power10/9105-22A?topic=ipmi-common-commands