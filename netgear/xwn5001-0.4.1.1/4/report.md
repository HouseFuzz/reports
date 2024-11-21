# xwn5001-0.4.1.1 DoS vulnerability
## firmware version
vendor: netgear

product: xwn5001

version: below or equal xwn5001-0.4.1.1

support url: https://www.netgear.com/support/product/xwn5001/#download

download url: https://www.downloads.netgear.com/files/GDC/XWN5001/XWN5001-V0.4.1.1.zip

## description
In netgear xwn5001-0.4.1.1, binary `/usr/sbin/uhttpd` contains a DoS vulnerability. Attackers can send malicious packet to trigger the vulnerability. The vulnerability lies in parsing and using paramater `plc_dev_select_num` in function `sub_43155C`.


## Impact
The vulnerability can cause Denial Of Service of the device.

## detail
In function `sub_43155C` (address: 0x43155C), the following code concats user's input containing `plc_dev_select_num` into local variable `v4`.
![alt text](image.png)

However, it didn't check whether `v4` is NULL or not before use and dereference it in `atoi`, causing potential NULL pointer dereference.


## poc
see [poc](./poc)

see [backtrace](./backtrce) for more information.
