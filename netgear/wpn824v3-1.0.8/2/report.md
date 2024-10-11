# wpn824v3-1.0.8 out-of-bound read vulnerability
## firmware version
vendor: netgear

product: wpn824v3

version: below or equal wpn824v3-1.0.8

## description
In netgear wpn824v3-1.0.8, binary `/bin/boa` contains a out-of-bound read and DoS vulnerability. Attackers can send malicious packet to trigger the vulnerability.

## detail
In function `get_mime_type` (address: 0x40A89C), the following loop doesn't check the boundry of the data, causing infinite loop , out-of-bound read and crash.

![oob](image.png)

## send packet
You can send the POC packet via TCP to the `80` port of the firmware's web server to trigger the vulnerability.

## poc
see [poc](./poc)

## screenshot
The qemu logging shows that the web server encounters a crash and SEGSEGV signal has triggered, and web server has stopped working. The pc indicates that there exists an out-of-bound read.

![crash](image-1.png)

## timeline
[24/10/11] report to vendor and CVE
