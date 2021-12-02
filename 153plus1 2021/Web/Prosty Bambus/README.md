# Prosty Bambus
**Category**: web \
**Points**: 100

## Desciption
Nie znam się za bardzo na tym całym JWT

## Solution
![](link do ss strony)
The very first thing we do is checking cookies and source code. \
There we find method creating JWT token, with sercet key which can get us simply everywhere.
```
if (!Cookies.get('gradeToken')) {
    const gradeToken = KJUR.jws.JWS.sign(null, {alg: "HS256", typ: "JWT"}, grade, "jRHLpurkTPDc6FXDSdYY4R3gyNjefZ89");
    Cookies.set('gradeToken', gradeToken);
}
```
We paste our current token from cookies to JWT token decoder ([jwt.io](jwt.io)). \
There we change value of Payload to 
```
{
  "grade": "6",
  "score": 100
}
```
And encode it with the secret key we found. \
Using our token in cookies gets us a flag!
## FLAG 
flag{takie_proste_jwt_na_rozgrzewke}