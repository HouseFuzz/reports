# wndrmac-1.0.0.10 DOS vulnerability
## firmware version
vendor: netgear

product: wndrmac

version: below or equal wndrmac-1.0.0.10

## description
In netgear wndrmac-1.0.0.10, binary `/usr/sbin/uhttpd` contains a DOS vulnerability. Attackers can send malicious packet to trigger the vulnerability. The vulnerability lies in the dereference of parameter retrived from `select_del_mac` in `config_qos_list_del`


## Impact
The vulnerability can cause Denial Of Service of the device.

## detail
In the address 0x43EC24 of `/usr/sbin/uhttpd`, the following  parses user's input containing `select_del_mac` into pointer `v4`. Then `v4` is dereferenced.
![alt text](image.png)

However, it didn't check whether the parameter `v4` is NULL or not before dereference, causing potential NULL pointer dereference.

## How to trigger
You can send the POC packet via TCP to the `80` port of the firmware's web server to trigger the vulnerability.

## poc
see [poc](./poc)

see [backtrace](./backtrace) for more information
