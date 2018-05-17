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


### 2. Generate a random number between 1 and 9 (including 1 and 9). Ask the user to guess the number, then tell them whether they guessed too low, too high, or exactly right. (Hint: remember to use the user input lessons from the very first exercise)

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


### 3. Write a Python program to convert height in centimeters to feet and inches.

```python
def height(cm):
  feet = int(cm / 30.48)
  inch = round(((cm % 30.48) / 2.54))
  y = "Your height is %s feet and %s inches." % (str(feet), str(inch))
  
  return y
  
print (height(int(input("What your height in cm?"))))
```

https://trinket.io/python/27bc58c127



### Tic Tac Toe


```python

gameon = True
p1_in_lst = []
p2_in_lst = []
while gameon:
    whole_lst = ['a1','a2','a3','b1','b2','b3','c1','c2','c3']

    win_lst_1 = ['aaa','bbb','ccc','111','222','333']
    win_lst_2 = ['abc','123']

    p1_in = str(input("Player One, please choose a place from " + str(whole_lst) +'.'))
    p1_in_lst.append(p1_in)
    whole_lst.remove(p1_in)
    print(p1_in_lst)

    p2_in = str(input("Player two, please choose a place from " + str(whole_lst) +'.'))
    p2_in_lst.append(p2_in)
    whole_lst.remove(p2_in)    
    print(p2_in_lst)


    if len(p1_in_lst) == 3 or len(p2_in_lst) == 3:
        p1_lst = sorted(p1_in_lst)
        p1_check = [p1_lst[0][0]+p1_lst[1][0]+p1_lst[2][0],p1_lst[0][1]+p1_lst[1][1]+p1_lst[2][1]]


        p2_lst = sorted(p2_in_lst)
        p2_check = [p2_lst[0][0]+p2_lst[1][0]+p2_lst[2][0],p2_lst[0][1]+p2_lst[1][1]+p2_lst[2][1]]


        if (p1_check[0] in win_lst_1) or (p1_check[0] in win_lst_2 and p1_check[1] in win_lst_2):
            print('Player1 wins!')
            
        break
        if (p2_check[0] in win_lst_1) or (p2_check[0] in win_lst_2 and p2_check[1] in win_lst_2):
            print('Player2 wins!')
            
        break



```
