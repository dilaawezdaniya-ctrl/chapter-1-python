# 🐍 Python — Dictionaries & Sets

> A complete beginner-friendly guide with real-world examples.  
> Part of my Python learning notes series.

---

## 📌 Table of Contents

1. [What are they?](#1-what-are-they)
2. [Dictionary — Deep Dive](#2-dictionary--deep-dive)
3. [Dictionary Methods](#3-dictionary-methods)
4. [Looping a Dictionary](#4-looping-a-dictionary)
5. [Dictionary Comprehension](#5-dictionary-comprehension)
6. [Nested Dictionary](#6-nested-dictionary)
7. [Set — Deep Dive](#7-set--deep-dive)
8. [Set Operations](#8-set-operations)
9. [Set Methods](#9-set-methods)
10. [Real-World Examples](#10-real-world-examples)
11. [Quick Reference Table](#11-quick-reference-table)

---

## 1. What are they?

### Dictionary
A dictionary stores data as **key → value pairs** — like a real dictionary where a word (key) maps to its meaning (value).

```python
student = {
    "name":  "Priya",
    "age":   20,
    "cgpa":  9.1
}
print(student["name"])   # Priya
```

### Set
A set is an **unordered collection of unique items** — duplicates are automatically removed.

```python
tags = {"python", "code", "python", "data"}
print(tags)   # {'python', 'code', 'data'}  ← duplicate removed!
```

---

## 2. Dictionary — Deep Dive

### Creating a Dictionary

```python
# Empty dictionary
empty = {}
empty = dict()

# With data
person = {
    "name":    "Rahul",
    "age":     21,
    "city":    "Indore",
    "is_student": True
}

# Using dict() constructor
person2 = dict(name="Priya", age=20, city="Mumbai")
```

### Accessing Values

```python
person = {"name": "Rahul", "age": 21, "city": "Indore"}

# Method 1 — square brackets (throws error if key missing)
print(person["name"])       # Rahul
# print(person["phone"])    # ❌ KeyError!

# Method 2 — .get() (safe, returns None if key missing)
print(person.get("name"))   # Rahul
print(person.get("phone"))  # None  ← no error!

# .get() with default value
print(person.get("phone", "Not provided"))   # Not provided
```

### Adding & Updating

```python
person = {"name": "Rahul", "age": 21}

# Add new key
person["city"] = "Indore"
print(person)   # {'name': 'Rahul', 'age': 21, 'city': 'Indore'}

# Update existing key
person["age"] = 22
print(person)   # {'name': 'Rahul', 'age': 22, 'city': 'Indore'}

# Update multiple at once
person.update({"age": 23, "city": "Mumbai", "cgpa": 9.1})
print(person)
```

### Removing Items

```python
person = {"name": "Rahul", "age": 21, "city": "Indore", "cgpa": 9.1}

# Remove by key — returns the value
removed = person.pop("cgpa")
print(removed)   # 9.1
print(person)    # {'name': 'Rahul', 'age': 21, 'city': 'Indore'}

# Remove last inserted item
person.popitem()
print(person)    # {'name': 'Rahul', 'age': 21}

# Delete by key
del person["age"]
print(person)    # {'name': 'Rahul'}

# Clear everything
person.clear()
print(person)    # {}
```

### Checking if Key Exists

```python
person = {"name": "Rahul", "age": 21}

print("name" in person)    # True
print("phone" in person)   # False
print("age" not in person) # False
```

---

## 3. Dictionary Methods

```python
student = {"name": "Priya", "age": 20, "cgpa": 9.1}

# .keys() — all keys
print(student.keys())     # dict_keys(['name', 'age', 'cgpa'])

# .values() — all values
print(student.values())   # dict_values(['Priya', 20, 9.1])

# .items() — all key-value pairs as tuples
print(student.items())    # dict_items([('name','Priya'),('age',20),('cgpa',9.1)])

# Convert to list
print(list(student.keys()))     # ['name', 'age', 'cgpa']
print(list(student.values()))   # ['Priya', 20, 9.1]

# .copy() — shallow copy
student2 = student.copy()

# .setdefault() — get value, or set it if key doesn't exist
student.setdefault("city", "Indore")
print(student["city"])   # Indore
```

---

## 4. Looping a Dictionary

```python
student = {"name": "Priya", "age": 20, "cgpa": 9.1}

# Loop over keys (default)
for key in student:
    print(key)

# Loop over values
for value in student.values():
    print(value)

# Loop over key-value pairs  ← most common!
for key, value in student.items():
    print(f"{key} → {value}")

# Output:
# name → Priya
# age  → 20
# cgpa → 9.1
```

---

## 5. Dictionary Comprehension

Just like list comprehension — a short way to build dictionaries.

```python
# Formula:
# {key: value for item in iterable if condition}

# Squares dictionary
squares = {x: x**2 for x in range(1, 6)}
print(squares)   # {1: 1, 2: 4, 3: 9, 4: 16, 5: 25}

# Filter — only even squares
even_sq = {x: x**2 for x in range(1, 11) if x % 2 == 0}
print(even_sq)   # {2: 4, 4: 16, 6: 36, 8: 64, 10: 100}

# Flip keys and values
original = {"a": 1, "b": 2, "c": 3}
flipped  = {v: k for k, v in original.items()}
print(flipped)   # {1: 'a', 2: 'b', 3: 'c'}

# Word length dictionary
words = ["apple", "banana", "kiwi"]
word_len = {word: len(word) for word in words}
print(word_len)  # {'apple': 5, 'banana': 6, 'kiwi': 4}
```

---

## 6. Nested Dictionary

A dictionary inside another dictionary.

```python
students = {
    "s001": {
        "name": "Priya",
        "age":  20,
        "marks": [88, 91, 95]
    },
    "s002": {
        "name": "Rahul",
        "age":  21,
        "marks": [76, 82, 88]
    }
}

# Access nested values
print(students["s001"]["name"])      # Priya
print(students["s002"]["marks"][0])  # 76

# Loop through nested dict
for roll, info in students.items():
    print(f"\nRoll: {roll}")
    print(f"  Name:  {info['name']}")
    print(f"  Age:   {info['age']}")
    print(f"  Marks: {info['marks']}")
```

---

## 7. Set — Deep Dive

### Creating a Set

```python
# Empty set — MUST use set(), NOT {}
empty = set()       # ✅ empty set
empty = {}          # ❌ this is an empty DICT, not set!

# With data
fruits  = {"apple", "banana", "mango"}
numbers = {1, 2, 3, 4, 5}
mixed   = {1, "hello", 3.14, True}

# From a list — removes duplicates automatically!
tags = set(["python", "code", "python", "data", "code"])
print(tags)   # {'python', 'code', 'data'}
```

### Key Properties of Sets

```python
my_set = {3, 1, 4, 1, 5, 9, 2, 6, 5}
print(my_set)   # {1, 2, 3, 4, 5, 6, 9}
#                  ↑ duplicates removed, order not guaranteed
```

> ⚠️ Sets are **unordered** — you cannot access items by index!
```python
my_set = {1, 2, 3}
# print(my_set[0])   # ❌ TypeError — no indexing in sets!
```

### Adding & Removing

```python
fruits = {"apple", "banana", "mango"}

# Add one item
fruits.add("cherry")
print(fruits)   # {'apple', 'banana', 'mango', 'cherry'}

# Add multiple items
fruits.update(["kiwi", "grape"])
print(fruits)

# Remove — raises error if not found
fruits.remove("banana")

# Discard — no error if not found (safer!)
fruits.discard("banana")   # no error even if already removed
fruits.discard("xyz")      # silently does nothing

# Pop — removes and returns a random item
popped = fruits.pop()
print(popped)   # some random item

# Clear everything
fruits.clear()
```

---

## 8. Set Operations

This is where sets **really shine** — mathematical operations.

```python
A = {1, 2, 3, 4, 5}
B = {4, 5, 6, 7, 8}
```

### Union — all items from both sets
```python
print(A | B)          # {1, 2, 3, 4, 5, 6, 7, 8}
print(A.union(B))     # same result
```

### Intersection — only items in BOTH sets
```python
print(A & B)               # {4, 5}
print(A.intersection(B))   # same result
```

### Difference — items in A but NOT in B
```python
print(A - B)              # {1, 2, 3}
print(A.difference(B))    # same result
print(B - A)              # {6, 7, 8}
```

### Symmetric Difference — items in either but NOT both
```python
print(A ^ B)                        # {1, 2, 3, 6, 7, 8}
print(A.symmetric_difference(B))    # same result
```

### Visual Picture
```
    A         B
  1  2  3 | 4  5 | 6  7  8
  ──────── | ──── | ────────
  A only   | Both | B only

Union      → everything:     {1,2,3,4,5,6,7,8}
Intersect  → middle only:    {4,5}
A - B      → A only:         {1,2,3}
B - A      → B only:         {6,7,8}
Sym. Diff  → sides only:     {1,2,3,6,7,8}
```

---

## 9. Set Methods

```python
A = {1, 2, 3, 4, 5}
B = {4, 5, 6}
C = {1, 2}

# Check if subset (C is inside A?)
print(C.issubset(A))      # True  — all of C is in A
print(C <= A)             # True  — same thing

# Check if superset (A contains C?)
print(A.issuperset(C))    # True  — A has everything in C
print(A >= C)             # True  — same thing

# Check if no common items
print(A.isdisjoint({9, 10}))   # True  — no overlap
print(A.isdisjoint(B))         # False — they share 4, 5

# Length
print(len(A))   # 5

# Membership
print(3 in A)   # True
print(9 in A)   # False

# Loop
for item in A:
    print(item)
```

---

## 10. Real-World Examples

### 🎓 Student Database → Dictionary
```python
students = {}

def add_student(roll, name, marks):
    students[roll] = {"name": name, "marks": marks}

def get_average(roll):
    marks = students[roll]["marks"]
    return sum(marks) / len(marks)

add_student(101, "Priya",  [88, 91, 95])
add_student(102, "Rahul",  [76, 82, 80])
add_student(103, "Aman",   [90, 88, 92])

print(f"Priya's avg: {get_average(101):.1f}")   # 91.3
print(f"Rahul's avg: {get_average(102):.1f}")   # 79.3

for roll, data in students.items():
    avg = sum(data["marks"]) / len(data["marks"])
    print(f"Roll {roll}: {data['name']} — Avg: {avg:.1f}")
```

---

### 🛒 Word Count → Dictionary
```python
sentence = "the cat sat on the mat the cat"
words    = sentence.split()

word_count = {}
for word in words:
    word_count[word] = word_count.get(word, 0) + 1

print(word_count)
# {'the': 3, 'cat': 2, 'sat': 1, 'on': 1, 'mat': 1}

# Most common word
most_common = max(word_count, key=word_count.get)
print(f"Most common: '{most_common}' ({word_count[most_common]} times)")
```

---

### 🎫 Remove Duplicates → Set
```python
# Visitors who came multiple times
visitors = ["Alice", "Bob", "Alice", "Charlie", "Bob", "Alice"]

unique_visitors = set(visitors)
print(f"Total visits:   {len(visitors)}")     # 6
print(f"Unique visitors:{len(unique_visitors)}")  # 3
print(unique_visitors)   # {'Alice', 'Bob', 'Charlie'}
```

---

### 🎮 Common Friends → Set Intersection
```python
rahul_friends  = {"Priya", "Aman", "Sneha", "Vikram"}
priya_friends  = {"Rahul", "Aman", "Neha",  "Sneha"}

common = rahul_friends & priya_friends
print("Common friends:", common)   # {'Aman', 'Sneha'}

only_rahul = rahul_friends - priya_friends
print("Only Rahul's:", only_rahul)   # {'Priya', 'Vikram'}
```

---

### 🏷️ Unique Tags → Set
```python
post1_tags = {"python", "coding", "beginners"}
post2_tags = {"python", "data",   "pandas"}
post3_tags = {"coding", "tips",   "beginners"}

# All unique tags across all posts
all_tags = post1_tags | post2_tags | post3_tags
print("All tags:", all_tags)

# Tags used in all posts
common_tags = post1_tags & post2_tags & post3_tags
print("Common tags:", common_tags)   # set() ← empty, none in all 3
```

---

## 11. Quick Reference Table

### Dictionary

| Feature | Code | Result |
|---|---|---|
| Create | `d = {"a": 1}` | dict |
| Access | `d["a"]` | `1` |
| Safe access | `d.get("a", 0)` | `1` or default |
| Add/Update | `d["b"] = 2` | adds key |
| Delete | `d.pop("a")` | removes & returns |
| All keys | `d.keys()` | dict_keys |
| All values | `d.values()` | dict_values |
| All pairs | `d.items()` | dict_items |
| Check key | `"a" in d` | True/False |
| Length | `len(d)` | int |
| Clear | `d.clear()` | `{}` |

### Set

| Feature | Code | Result |
|---|---|---|
| Create | `s = {1, 2, 3}` | set |
| Empty set | `s = set()` | set (NOT `{}`) |
| Add | `s.add(4)` | adds item |
| Remove (safe) | `s.discard(4)` | removes silently |
| Union | `A \| B` | all items |
| Intersection | `A & B` | common items |
| Difference | `A - B` | A only items |
| Sym. Diff | `A ^ B` | non-common items |
| Membership | `3 in s` | True/False |
| Length | `len(s)` | int |
| No duplicates | automatic | always unique |
| No indexing | `s[0]` → ❌ | TypeError |

---

### 🏁 When to Use What?

```
Need key → value lookup?        →  Dictionary  { key: value }
Need unique items only?         →  Set         { item }
Need to find common items?      →  Set (intersection)
Need to count occurrences?      →  Dictionary
Need ordered data with index?   →  List  [ ]
Need fixed data?                →  Tuple ( )
```

---

> 📝 *These notes are part of my Python fundamentals series.*  
> ⭐ *If this helped you, consider starring the repo!*
