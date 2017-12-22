**1.遍历相同 key 的 value 存为 list**

```python
import collections

test_data = [('a', 1), ('b', 2), ('c', 3), ('a', 4)]
test_dict = collections.defaultdict(list)
for i in test_data:
    k, v = i
    test_dict[k].append(v)
```

**2.任意进制转换**

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
**3.返回可读的文件大小**

```python
def humanize_bytes(bytesize, precision=2):
    abbrevs = (
        (1 << 50, 'PB'),
        (1 << 40, 'TB'),
        (1 << 30, 'GB'),
        (1 << 20, 'MB'),
        (1 << 10, 'kB'),
        (1, 'bytes')
    )
    if bytesize == 1:
        return '1 byte'
    for factor, suffix in abbrevs:
        if bytesize >= factor:
            break
    return '%.*f %s' % (precision, bytesize / factor, suffix)
```

**4.获取文件的文件目录**

```python
import os
from functools import partial

get_file_path = partial(os.path.join, HERE, UPLOAD_FOLDER)
```

**5.获取文件的MD5**

```python 
import hashlib

def get_file_md5(f, chunk_size=8192):
    h = hashlib.md5()
    while True:
        chunk = f.read(chunk_size)
        if not chunk:
            break
        h.update(chunk)
    return h.hexdigest()
```

