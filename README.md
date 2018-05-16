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
    
print(task(18))
  ```
https://trinket.io/python/a425cde61c


### 1. Generate a random number between 1 and 9 (including 1 and 9). Ask the user to guess the number, then tell them whether they guessed too low, too high, or exactly right. (Hint: remember to use the user input lessons from the very first exercise)

Extras:

Keep the game going until the user types “exit”
Keep track of how many guesses the user has taken, and when the game ends, print this out.

```python
import random
gameon = True
onemore='yes'
target=random.randint(1,9)
plays=[]

while onemore=='yes':
  guess=int(input('Guess a number between 1 to 9.'))
  plays.append(guess)
  
  if guess < 1 or guess > 9:
    print('Out of bound!')
    break
    
  if guess != target:
    if guess < target:
      print("Too small!") 
    if guess > target:
      print("Too large!") 
    onemore = input("One more guess? Type 'yes' or 'no'.")

  if guess == target:
    if len(plays)==1:
      print('You got it right in oneshot!')
    else:
      print('You got it right in {} guesses.'.format(len(plays)))

    break
```

https://trinket.io/python/2b8ea10f7d
