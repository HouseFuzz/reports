# wnce4004-1.0.0.22 stack-based buffer overflow vulnerability
## firmware information
vendor: netgear

product: wnce4004

version: below or equal wnce4004-1.0.0.22

support url: https://www.netgear.com/support/product/wnce4004/#download

firmware download url: https://www.downloads.netgear.com/files/GDC/WNCE4004/WNCE4004_V1.0.0.22.zip

## description
In netgear wnce4004-1.0.0.22, binary `/usr/sbin/uhttpd` contains a stack-based buffer overflow vulnerability at address 0x406730. Attackers can send malicious packet to trigger the vulnerability.'

## Impact
The vulnerability can cause Denial Of Service of the device or arbitary code execution.

## Detail
In function `sub_406730`(address: 0x406730), it concated user's input into local stack buffer, without checking its length. This results in stack-based buffer overflow
![alt text](image-1.png)

## POC
see [poc](./poc)

You can refer to qemu [backtrace](./backtrace) for further information.
