# Mainframe leak
**Category**: reversing
**Points**: 350

## Description
Nasi agenci przechwycili ten zdekompilowany kod, który wedle naszych ustaleń powinien generować flagę. Czy jesteś w stanie ją odzyskać?

## Solution
After downloading the file, we are presented with a code that resembles Python Assembly code. My first thought was to find a tool that will convert it to normal Python. Some time passed, and I found a tool on PyPI called xasm. Unfortunetly, it used slightly different format than what was in the challenge and I had no way to make it work. At that point, I decided to do it by hand with the help of dis module. The idea was to disassemble the program after writing every line of code and compare it with given input. Through trial and error (and Python docs) I managed to write this piece of code which generates the flag.

```py
import dis

def main():
    n = [36054, 55674, 30924, 59454, 53145, 99144, 95364, 97605, 93024, 97605, 15984, 78084, 13644, 93024, 74205, 13644, 30924, 55674, 93024, 99144, 95364, 97605, 38394, 55674, 13644, 30924, 97605, 34515, 74205, 13644, 99945]
    for i, x in enumerate(n):
        n[i] = int(str(n[i])[::-1])
        n[i] -= 18
        n[i] //= 432
    o = ''
    for p in n:
        o += chr(p-2)
    return o
        

print(dis.dis(main))
print(main())
```

## FLAG
flag{dis_some_real_displeasure}