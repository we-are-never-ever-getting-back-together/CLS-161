---
layout: post
title: Exercises Ch. 5
description: Select exercises from Python Crash Course
---

# Python Crash Course Chapter 5

## 5-1. Conditional Tests

Write a series of conditional tests. Print a statement describing each test and your prediction for the results of each test.

```python
author = 'Murakami'
print("Is author == 'Murakami'? I predict True.")
print(author == 'TMurakami')
```

    Is author == 'Murakami'? I predict True.
    False

```python
author = 'Toni Morrison'
print("Is author != 'Toni Morrison'? I predict False.")
print(author != 'Toni Morrison')
```

    Is author != 'Toni Morrison'? I predict False.
    False

```python
a = 1
b = 2
print("Is a > b? I predict False.")
print(a > b)
```

    Is a > b? I predict False.
    False

```python
historian = "Isabel Wilkerson"
print("Is historian == 'isabel wilkerson'? I predict False.")
print(historian == "isalbel wilkerson")
```

    Is historian == 'isabel wilkerson'? I predict False.
    False

```python
historian = "Isabel Wilkerson"
print("Is historian != 'isabel wilkerson'? I predict True.")
print(historian != "isalbel wilkerson")
```

    Is historian != 'isabel wilkerson'? I predict True.
    True

## 5-2. More Conditional Tests

You don’t have to limit the number of tests you create to ten. If you want to try more comparisons, write more tests and add them to conditional_tests.py. Have at least one True and one False result for each of the following:

- Tests for equality and inequality with strings
- Tests using the `lower()` method
- Numerical tests involving equality and inequality, greater than and less than, greater than or equal to, and less than or equal to
- Tests using the `and` keyword and the `or` keyword
- Test whether an item is in a list
- Test whether an item is not in a list

```python
# Tests for equality and inequality with strings
title = "The Warmth of Other Suns"
print("Is title == 'the warmth of other suns'? I predict False.")
print(title == 'the warmth of other suns')
```

    Is title == 'the warmth of other suns'? I predict False.
    False

```python
# Tests using the lower() method
title = "The Warmth of Other Suns"
print("Is title.lower() == 'the warmth of other suns'? I predict True.")
print(title.lower() == 'the warmth of other suns')
```

    Is title.lower() == 'the warmth of other suns'? I predict True.
    True

```python
# Numerical tests involving equality and inequality, greater than and less than, greater than or equal to,
# and less than or equal to
print("Is 4 == 2 * 2? I predict True.")
print(4 == 2 * 2)
print("\n")
print("Is 2 < 1? I predict False." )
print( 2 < 1)
print("\n")
print("Is 134 >= 16? I predict True.")
```

    Is 4 == 2 * 2? I predict True.
    True


    Is 2 < 1? I predict False.
    False


    Is 134 >= 16? I predict True.

```python
# Tests using the and keyword and the or keyword
print("Is 15 == 15 and 125 > 130? I predict False.")
print(15 == 15 and 125 > 130)
print("\n")
print("Is 15 == 15 or 125 > 130? I predict True.")
print(15 == 15 or 125 > 130)
```

    Is 15 == 15 and 125 > 130? I predict False.
    False


    Is 15 == 15 or 125 > 130? I predict True.
    True

```python
# Test whether an item is in a list
philosophers = ["Hypatia", "Arendt", "Nussbaum"]
print("Is 'Hume' in philosophers? I predict False")
print("Hume" in philosophers)
```

    Is 'Hume' in philosophers? I predict False
    False

```python
# Test whether an item is not in a list
philosophers = ["Hypatia", "Arendt", "Nussbaum"]
print("Is 'Hume' not in philosophers? I predict True")
print("Hume" not in philosophers)
```

    Is 'Hume' not in philosophers? I predict True
    True

## 5-6. Stages of Life

Write an if-elif-else chain that determines a person’s stage of life. Set a value for the variable age, and then:

- If the person is less than 2 years old, print a message that the person is a baby.
- If the person is at least 2 years old but less than 4, print a message that the person is a toddler.
- If the person is at least 4 years old but less than 13, print a message that the person is a kid.
- If the person is at least 13 years old but less than 20, print a message that the person is a teenager.
- If the person is at least 20 years old but less than 65, print a message that the person is an adult.
- If the person is age 65 or older, print a message that the person is an elder.

```python
age = 41
if age < 2:
    print("You are a baby.")
elif age >= 2 and age < 4:
    print("You are a toddler.")
elif age >=4 and age < 13:
    print("You are a kid.")
elif age >= 13 and age < 20:
    print("You are a teenager.")
elif age >=20 and age < 65:
    print("You are an adult.")
else:
    print("You are an elder")
```

    You are an adult.

## 5-7. Favorite Fruit

Make a list of your favorite fruits, and then write a series of independent if statements that check for certain fruits in your list.

- Make a list of your three favorite fruits and call it favorite_fruits.
- Write five if statements. Each should check whether a certain kind of fruit is in your list. If the fruit is in your list, the if block should print a statement, such as You really like bananas!

```python
favorite_fruits = ["kiwi", "tangerine", "blueberry"]

if "kiwi" in favorite_fruits:
    print("I really like kiwis")

if "banana" in favorite_fruits:
    print("I really like bananas")

if "tangerine" in favorite_fruits:
    print("I really like tangerines")

if "blueberry" in favorite_fruits:
    print("I really like blueberries")

if "apple" in favorite_fruits:
    print("I really like apples")
```

    I really like kiwis
    I really like tangerines
    I really like blueberries

## 5-8. Hello Admin

Make a list of five or more usernames, including the name 'admin'. Imagine you are writing code that will print a greeting to each user after they log in to a website. Loop through the list, and print a greeting to each user:

- If the username is 'admin', print a special greeting, such as Hello admin, would you like to see a status report?
- Otherwise, print a generic greeting, such as Hello Jaden, thank you for logging in again.

```python
usernames = ['admin', 'incel_45', 'm_saxton', 'user_35873', '2legit']

for username in usernames:
    if username == 'admin':
        print(f"Hello {username}, would you like to see a status report?")
    else:
        print(f"Hello {username}, thank you for logging in again.")
```

    Hello admin, would you like to see a status report?
    Hello incel_45, thank you for logging in again.
    Hello m_saxton, thank you for logging in again.
    Hello user_35873, thank you for logging in again.
    Hello 2legit, thank you for logging in again.

## 5-9. No Users

Add an if test to hello_admin to make sure the list of users is not empty.

- If the list is empty, print the message We need to find some users!
- Remove all of the usernames from your list, and make sure the correct message is printed.

```python
usernames = ['admin', 'incel_45', 'm_saxton', 'user_35873', '2legit']
usernames.clear()  # this is one way to clear a list

if usernames:
    for username in usernames:
        if username == 'admin':
            print(f"Hello {username}, would you like to see a status report?")
        else:
            print(f"Hello {username}, thank you for logging in again.")
else:
    print("We need to find some users!")
```

    We need to find some users!

## 5-10. Checking Usernames

Do the following to create a program that simulates how websites ensure that everyone has a unique username.

- Make a list of five or more usernames called current_users.
- Make another list of five usernames called new_users. Make sure one or two of the new usernames are also in the current_users list.
- Loop through the new_users list to see if each new username has already been used. If it has, print a message that the person will need to enter a new username. If a username has not been used, print a message saying that the username is available.
- Make sure your comparison is case insensitive. If 'John' has been used, 'JOHN' should not be accepted. (To do this, you’ll need to make a copy of current_users containing the lowercase versions of all existing users.)

```python
# Make a list of five or more usernames called current_users.
current_users = ['admin', 'incel_45', 'm_saxton', 'user_35873', '2legit']

#Make another list of five usernames called new_users.
# Make sure one or two of the new usernames are also in the current_users list.
new_users = ['cool_cat', '2legit', 'the_ddue', 'm_saxton', 'DH_pro']

# Loop through the new_users list to see if each new username has already been used.
#If it has, print a message that the person will need to enter a new username.
#If a username has not been used, print a message saying that the username is available.

for username in new_users:
    if username.lower() in current_users:
        print(f"{username} is not available, please choose a new username.")
    else:
        print(f"{username} is available.")
```

    cool_cat is available.
    2legit is not available, please choose a new username.
    the_ddue is available.
    m_saxton is not available, please choose a new username.
    DH_pro is available.

```python

```
