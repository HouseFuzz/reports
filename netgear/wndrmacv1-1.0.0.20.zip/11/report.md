# wndrmacv1-1.0.0.20 DOS vulnerability
## firmware version
vendor: netgear

product: wndrmacv1

version: below or equal wndrmacv1-1.0.0.20

## description
In netgear wndrmacv1-1.0.0.20, binary `/usr/sbin/uhttpd` contains a DOS vulnerability. Attackers can send malicious packet to trigger the vulnerability. The vulnerability lies the dereference of parameter `rm_access` in `config_remote`(address: 0x43BB2C)

## Impact
The vulnerability can cause Denial Of Service of the device.

## detail
In function `config_remote` (address: 0x43BB2C), the following code parses user's input containing `rm_access` into `v8`. Then `v8` is dereferenced and used in `strcmp` without checking whether it's NULL or not, causing potential NULL pointer dereference.
![alt text](image.png)

## poc
see [poc](./poc)

see [backtrace](./backtrace) for more information.