# CAN Bus

# Usage

## Bring up CAN interface

```bash
sudo ip link set can0 up type can bitrate 1000000
```

Check status by ``ifconfig``

```bash
ifconfig
# you will see same like this:
# can0: flags=193<UP,RUNNING,NOARP>  mtu 16
#       unspec 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  txqueuelen 10  (UNSPEC)
#       RX packets 4  bytes 32 (32.0 B)
#       RX errors 0  dropped 0  overruns 0  frame 0
#       TX packets 4  bytes 32 (32.0 B)
#       TX errors 1  dropped 1 overruns 0  carrier 1  collisions 0
```

## Loopback test

```bash
sudo ip link set can0 down
sudo ip link set can0 type can loopback on
sudo ip link set can0 up type can bitrate 1000000
```

Now open two terminals, one as sender and one as receiver.

In receiver terminal:

```bash
candump can0 
```

In sender terminal:

```bash
cansend can0 123#aabbccdd
cansend can0 123#12345678
```
## More commands

```bash
ip link set can0 up type can help
```

# Reference

[CAN Bus in Linux](https://wiki.rdu.im/_pages/Application-Notes/Software/can-bus-in-linux.html)