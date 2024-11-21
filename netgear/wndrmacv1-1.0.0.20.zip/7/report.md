# wndrmacv1-1.0.0.20 stack-based buffer overflow vulnerability
## firmware version
vendor: netgear

product: wndrmacv1

version: below or equal wndrmacv1-1.0.0.20

support url: https://www.netgear.com/support/product/wndrmacv1/#download

firmware download url: https://www.downloads.netgear.com/files/GDC/WNDRMACv1/WNDRMAC%20Firmware%20Version%201.0.0.20.zip

## description
In netgear wndrmacv1-1.0.0.20, binary `/usr/sbin/uhttpd` contains a Dstack-based buffer overflowOS vulnerability. Attackers can send malicious packet to trigger the vulnerability. The vulnerability lies in function `do_js`.

## Impact
The vulnerability can cause Denial Of Service of the device, or arbitary code execution.

## detail
In function `do_js` (address: 0x408AA8), the following code concats user's input into a stack-based buffer `v15` without checking its length, causing potential stack-based buffer overflow.
![alt text](image.png)

## poc
see [poc](./poc)

see [backtrace](./backtrace) for more information.