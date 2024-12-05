# XOR without using ^ operator

```
int xor(const int x, const int y) {
   return (x | y) & (~x | ~y);
}
```
