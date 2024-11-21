# wndrmacv1-1.0.0.20 DOS vulnerability
## firmware version
vendor: netgear

product: wndrmacv1

version: below or equal wndrmacv1-1.0.0.20

## description
In netgear wndrmacv1-1.0.0.20, binary `/usr/sbin/uhttpd` contains a DOS vulnerability. Attackers can send malicious packet to trigger the vulnerability. The vulnerability lies the use of parameter retrived from `attached_mac` in `config_add_qos_mac`(address: 0x439638)

## Impact
The vulnerability can cause Denial Of Service of the device.

## detail
In function `config_add_qos_mac` (address: 0x439638), the following code parses user's input containing `attached_mac` into `v4`. Then `v4` is used as a parameter of `strcmp` without checking whether it's NULL or not, causing potential NULL pointer dereference.
![alt text](image.png)