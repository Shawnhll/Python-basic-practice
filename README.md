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

### Input integers for x,y,z,n and list all the possible cordinates of (a,b,c) if a+b+c != n; 0 <= a,b,c <= x,y,z respecively. 



```python
x,y,z,n = (int(input()) for _ in range(4))
print([[a,b,c] for a in range(x+1) for b in range(y+1) for c in range(z+1) if a + b + c != n])

```

https://trinket.io/python3/2a06c1d0fd




### Convert temperatures to and from celsius, fahrenheit.



```python

def choose():
  return int(input('What would you like to convert? \n1. From C to F. \n2. From F to C.'))

def c2f():
  c = int(input("What's the temperature in C do you want to convert to F?"))
  f = int(c*9/5 + 32)
  print(str(c)+' C equals to '+str(f)+' F.')
  return f
  
def f2c():
  f = int(input("What's the temperature in F do you want to convert to C?"))
  c = int((5/9) * (f - 32))
  print(str(f)+' F equals to '+str(c)+' C.')
  return c
  
def gameonoff():
  while True:
    x = int(input("Want to convert another temperature? Input 1 if yes, 2 if no."))
    if x == 1:
      return True
      break
    elif x == 2:
      return False
      break
    else:
      print('Unrecogonized input, please try again.')
      pass
  
while True:
  if choose() == 1:
    c2f()
  else:
    f2c()
  
  if not gameonoff():
    print('Thank you for using this tool.')
    break

```

https://trinket.io/python/4b51882e11



### Printing string and integer (or float) in the same line

```python

x = 8
# to give the same output: The number is 8.

print('The number is', x, end='.\n')

print('The number is ' + str(x)+".")

print('The number is %s.' % x)

print(f'The number is {x}.') # works on in version 3.6 or later

print('The number is {}.'.format(x))
```

https://trinket.io/python3/e56cb6709b



### Write a Python program to check the validity of a password (input from users).

Validation :

 At least 1 letter between [a-z] and 1 letter between [A-Z].<br />
 At least 1 number between [0-9].<br />
 At least 1 character from [$#@].<br />
 Minimum length 6 characters.<br />
 Maximum length 16 characters.


```python

import re
p= input("Input your password")
x = True
while x:  
    if (len(p)<6 or len(p)>12):
        break
    elif not re.search("[a-z]",p):
        break
    elif not re.search("[0-9]",p):
        break
    elif not re.search("[A-Z]",p):
        break
    elif not re.search("[$#@]",p):
        break
    elif re.search("\s",p):
        break
    else:
        print("Valid Password")
        x=False
        break

if x:
    print("Not a Valid Password")

```

https://trinket.io/python3/2495ba3ab8


###Ending a Program Early with sys.exit()


```python

import sys

while True:
    print('Type exit to exit.')
    response = input()
    if response == 'exit':
        sys.exit()
    print('You typed ' + response + '.')
```

https://trinket.io/python3/045a24e05e



