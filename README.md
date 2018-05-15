Python-basic-practice
==
### 1. Identify and save all the prime numbers in a range from 0 to num into a list called lst.

```python
def task(num):
  num = int(num)
  lst = []
  
  if num < 2:
    return lst

  if num >= 2:
    lst.append(2)

  for i in range(3, num + 1):       
    if i % 2 == 1:
      switch = True
      for n in range(3, int(i ** 0.5) + 1, 2):
        if i % n == 0:
          switch = False  
          break        
      if switch:
        lst.append(i)
          
  return lst
  ```
