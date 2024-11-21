# wpn824v3-1.0.8 out-of-bound read vulnerability
## firmware version
vendor: netgear

product: wpn824v3

version: below or equal wpn824v3-1.0.8

support url: https://www.netgear.com/support/product/wpn824v3/#download

firmware download url: https://www.downloads.netgear.com/files/GDC/WPN824V3/WPN824V3-V1.0.8_1.0.7NA.zip

## description
In netgear wpn824v3-1.0.8, binary `/bin/boa` contains a stack-based buffer out-of-bound read and DoS vulnerability. Attackers can send malicious packet to trigger the vulnerability.

## detail
In function `find_alias` (address: 0x406230), the following loop doesn't check the boundry of the data, causing infinite loop , out-of-bound read and crash.

![oob-r](image.png)

## send packet
You can send the POC packet via TCP to the `80` port of the firmware's web server to trigger the vulnerability.

## poc
see [poc](./poc)

## screenshot
The qemu logging shows that the web server encounters a crash and SEGSEGV signal has triggered, and web server has stoppod working. The pc indicates that there exists an out-of-bound read.

![crash](image-1.png)
