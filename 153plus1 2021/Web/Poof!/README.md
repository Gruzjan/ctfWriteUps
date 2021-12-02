# Poof!
**Category**: web \
**Points**: 100

## Desciption
Znalazłem w internecie taki dziwny teleturniej, może uda Ci się wygrać flagę?

## Solution
![](link do ss strony)
In this challenge we have to change specific http headers we send when accessing the website.
###lvl 1
"Tylko Netscape Navigator może wyświetlić tą stronę" Change our user agent to Netscape Navigator. \
User-Agent: Netscape Navigator
###lvl 2
"Musisz mieć ciasteczko z wartością user równą &#x27;admin&#x27;" Add cookie user with value admin. \
Cookie: user = admin
###lvl 3
"Tylko język francuski na tej stronie!" Change the requested language. \
Accept-Language: fr
###lvl 4
"Musisz połączyć się z adresu IP 123.123.123.123" Change our ip adress. \
X-Forwarded-For: 123.123.123.123
###lvl 5
"Udało się! Użyj metody SPOOF na tej stronie aby otrzymać flagę!" Change GET method to SPOOF. \
SPOOF /poziom5 HTTP/1.1

## FLAG 
flag{p00f_podstawy_manipulacji}