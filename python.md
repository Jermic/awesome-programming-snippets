**1. [Dict] 遍历相同 key 的 value 存为 list**

```python
import collections

test_data = [('a', 1), ('b', 2), ('c', 3), ('a', 4)]
test_dict = collections.defaultdict(list)
for i in test_data:
    k, v = i
    test_dict[k].append(v)
```

**2. 任意进制转换**

```python
# 1.Parsing string with base into a number is easy  
num = int(str, radix)  

# 2.We have to write our own function for outputting to string with arbitrary base  
def itoa(num, radix):  
  result = ""  
  while num > 0:  
    result = "0123456789abcdefghijklmnopqrstuvwxyz"[num % radix] + result  
    num /= radix  
  return result  

def base_to(num, b):
    return ((num == 0) and "0") or (base_to(num // b, b).lstrip("0") + "0123456789abcdefghijklmnopqrstuvwxyz"[num % b])
```