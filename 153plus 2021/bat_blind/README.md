# bat blind
**Category**: web \
**Points**: 300

## Description
This website was developed by a blind bat. I was able to steal one of their accounts. You can login with bat and odvqhU378. But I don't get it, the site just tells you if you're logged in or not.

Note: The flag is in the flags table in the flag column, not the users table...


## Solution
In the description there is a small hint that we will be dealing with blind SQL injection. We also got login and a password to login. After trying to log in we are only getting information about whether it was successful or not. Next step was to try some SQL payloads and see if something works. I managed to craft this one

```sql
bat' AND SUBSTRING((SELECT flag FROM flags WHERE flag LIKE "f%"),1,1)>'a
```

It displays that we logged in, so the SQL statement evaluated to true. Then I created (very shitty) Python script to brute force the flag.

```py
kodzik na laptopie pozniej go wrzuce
```

## FLAG
flag{but_you_were_blind_as_a_bat}