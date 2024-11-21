# wndrmacv1-1.0.0.20 DOS vulnerability
## firmware version
vendor: netgear

product: wndrmacv1

version: below or equal wndrmacv1-1.0.0.20

support url: https://www.netgear.com/support/product/wndrmacv1/#download

firmware download url: https://www.downloads.netgear.com/files/GDC/WNDRMACv1/WNDRMAC%20Firmware%20Version%201.0.0.20.zip

## description
In netgear wndrmacv1-1.0.0.20, binary `/usr/sbin/uhttpd` contains a DOS vulnerability. Attackers can send malicious packet to trigger the vulnerability. The vulnerability lies the dereference of parameter `skeyword` in `config_block_sites`(address: 0x439B00)

## Impact
The vulnerability can cause Denial Of Service of the device.

## detail
In function `config_block_sites` (address: 0x439770), the following code parses user's input containing `skeyword` into `v4`. Then `v4` is used and dereferenced in `strcmp` without checking whether it's NULL or not, causing potential NULL pointer dereference.
![alt text](image.png)
