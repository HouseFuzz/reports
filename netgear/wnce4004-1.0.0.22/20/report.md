# wnce4004-1.0.0.22 DOS vulnerability
## firmware version
vendor: netgear

product: wnce4004

version: below or equal wnce4004-1.0.0.22

support url: https://www.netgear.com/support/product/wnce4004/#download

firmware download url: https://www.downloads.netgear.com/files/GDC/WNCE4004/WNCE4004_V1.0.0.22.zip

## description
In netgear wnce4004-1.0.0.22, binary `/usr/sbin/uhttpd` contains a DOS vulnerability. Attackers can send malicious packet to trigger the vulnerability. The vulnerability's root cause is NULL pointer dereference in function `strstr` in `handle_request`

## Impact
The vulnerability can cause Denial Of Service of the device.

## detail
In the address 0x404A9C of `/usr/sbin/uhttpd`, the following  parses user's input containing a space and check whether it's content is `%20timestamp=`
![alt text](image.png)

However, it didn't check whether the parameter `v89` is NULL or not before putting it as a argument of `strstr` , causing potential NULL pointer dereference.


