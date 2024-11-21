# wndrmacv1-1.0.0.20 DOS vulnerability
## firmware version
vendor: netgear

product: wndrmacv1

version: below or equal wndrmacv1-1.0.0.20

support url: https://www.netgear.com/support/product/wndrmacv1/#download

firmware download url: https://www.downloads.netgear.com/files/GDC/WNDRMACv1/WNDRMAC%20Firmware%20Version%201.0.0.20.zip

## description
In netgear wndrmacv1-1.0.0.20, binary `/usr/sbin/uhttpd` contains a DOS vulnerability. Attackers can send malicious packet to trigger the vulnerability. The vulnerability lies in the dereference of parameter in `cmd_wifi_coexist`

## Impact
The vulnerability can cause Denial Of Service of the device.

## detail
In the address 0x40DE14 of `/usr/sbin/uhttpd`, the following code parses user's input in of `hidd_coexist_flag` into `dword_1000D080` (at address 0x1000D080). The result of cgi_request() may be NULL if parameter is not presented in user's input.
![alt text](image.png)

The global_var is then used in `cgi_commit` to invoke cgi requests.
![alt text](image-1.png)

However, in function  `cmd_wifi_coexist`, the following code didn't check whether the argument(which is `dword_1000D080`) before dereference it. It may cause NULL pointer dereference and Denial Of Service.
![alt text](image-2.png)

## POC
see [poc](./poc)

see [backtrace](./backtrace) for more information

