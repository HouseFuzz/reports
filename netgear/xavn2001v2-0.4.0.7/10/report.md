# xavn2001v2-0.4.0.7 stack-based buffer overflow vulnerability
## firmware version
vendor: netgear

product: xavn2001v2

version: below or equal xavn2001v2-0.4.0.7

## description
In netgear xavn2001v2-0.4.0.7, binary `/usr/sbin/uhttpd` contains a stack-based buffer overflow vulnerability. Attackers can send malicious packet to trigger the vulnerability. The problem lies in function `sub_40FA88`.

## Impact
The vulnerability can cause Denial Of Service of the device, or even arbitary code execution.

## detail
In function `sub_40FA88` (address: 0x40FA88), the following code concats user's input into local variable `v20`, which is a stack-based variable with limited size 128 bytes.
![alt text](image.png)

However, it didn't check whether length of input from user is below 128 bytes. Causing potential stack-based buffer overflow. 



## poc
see [poc](./poc)

see [backtrace](./backtrace) for more information.
