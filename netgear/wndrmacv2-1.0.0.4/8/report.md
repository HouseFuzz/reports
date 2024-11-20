# wndrmacv2-1.0.0.4 DoS vulnerability
## firmware version
vendor: netgear

product: wndrmacv2

version: below or equal wndrmacv2-1.0.0.4

## description
In netgear wndrmacv2-1.0.0.4, binary `/usr/sbin/uhttpd` contains a NULL pointer dereference vulnerability in `config_qosmac_del`. Attackers can send malicious packet to trigger the vulnerability.

## Impact
Attackers can send malicious packet to trigger the vulnerability, causing Denial Of Service.

## detail
In function `config_qosmac_del` (address: 0x439A4C), the following code parses user's input containing `select_qoslist_num` into `v4`. Then `v8` is used and dereferenced without checking it's NULL or not, causing potential NULL pointer dereference
![alt text](image.png)


## poc
see [poc](./poc)

see [backtrace](./backtrace) for more information.
