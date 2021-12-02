# PanTadeusz(.out)
**Category**: reversing \
**Points**: 50

## Description
Chiałbym, abyś przeczytał tę konkretną wersję "Pana Tadeusza"

## Solution
Running strings with grep reveals a flag.
```
strings pantadeusz | grep flag
```

## FLAG
flag{pan_tadeusz_na_maturze_2022_potwierdzone_info}