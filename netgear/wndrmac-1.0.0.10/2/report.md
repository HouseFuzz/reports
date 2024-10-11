# wndrmac-1.0.0.10 DOS vulnerability
## firmware version
vendor: netgear

product: wndrmac

version: below or equal wndrmac-1.0.0.10

## description
In netgear wndrmac-1.0.0.10, binary `/usr/sbin/uhttpd` contains a DOS vulnerability. Attackers can send malicious packet to trigger the vulnerability.

## detail
In function `config_add_qos_mac` (address: 0x43EAEC), malicious TCP packet will trigger NULL pointer dereference and cause DoS. The parameter of `strcmp` maybe NULL and it will cause NULL pointer dereference.
![strcmp](image-1.png)

## send packet
You can send the POC packet via TCP to the `80` port of the firmware's web server to trigger the vulnerability.

## poc
see [poc](./poc)

## screenshot
The qemu logging shows that the web server encounters a crash and SEGSEGV signal has triggered, and web server has stoppod working.

![crash](image.png)

## timeline
[24/10/11] report to vendor and CVE
