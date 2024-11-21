# wndr3700v2-1.0.0.8 stack-based buffer overflow vulnerability
## firmware version
vendor: netgear

product: wndr3700v2

version: below or equal wndr3700v2-1.0.0.8

## description
In netgear wndr3700v2-1.0.0.8, binary `/usr/sbin/uhttpd` contains a stack-based buffer overflow vulnerability. Attackers can send malicious packet to trigger the vulnerability. The problem lies in function `do_js`.

## Impact
The vulnerability can cause Denial Of Service of the device, or even arbitary code execution.

## detail
In function `do_js` (address: 0x4052EC), the following code concats user's input into local variable `v15`, which is a stack-based variable with limited size.
![alt text](image.png)


However, it didn't check the length of input from user, Causing potential stack-based buffer overflow. 



## poc
see [poc](./poc)
