# wndrmac-1.0.0.10 DOS vulnerability
## firmware version
vendor: netgear

product: wndrmac

version: below or equal wndrmac-1.0.0.10

## description
In netgear wndrmac-1.0.0.10, binary `/usr/sbin/uhttpd` contains a DOS vulnerability. Attackers can send malicious packet to trigger the vulnerability.

## detail
In function `cgi_request` (address: 0x431C4C), malicious TCP packet will trigger NULL pointer dereference and cause DoS. The parameter of `strtoul` may be NULL, which will trigger the vulnerability.
![strtoul](image.png)

## send packet
You can send the POC packet via TCP to the `80` port of the firmware's web server to trigger the vulnerability.

## poc
see [poc](./poc)

## screenshot
The qemu logging shows that the web server encounters a crash and SEGSEGV signal has triggered, and web server has stoppod working.

![crash](image-1.png)