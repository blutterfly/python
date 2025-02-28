## Dictionary Best Practice

~~~python
### Checking if a key exists

my_dict = {"name": "Kiran", "age": 24}
if "name" in my_dict:
    print(my_dict["name"])
else:
    print("No name found")

my_dict = {"name": "Kiran", "age": 24}
print(my_dict.get("name", "No name found"))

### Looping over keys and values

my_dict = {"a": 1, "b": 2, "c": 3}
for key in my_dict:
    print(key, my_dict[key])

for key, value in my_dict.items():
    print(key, value)

### Merging dictionaries

dict1 = {"a": 1, "b": 2}
dict2 = {"b": 3, "c": 4}
dict1.update(dict2)
print(dict1)

dict1 = {"a": 1, "b": 2}
dict2 = {"b": 3, "c": 4}
new_dict = {**dict1, **dict2}
print(new_dict)  # {'a': 1, 'b': 3, 'c': 4}

### Using defaultdict

from collections import defaultdict
my_dict = defaultdict(int)
my_dict["a"] += 1  # Works, but is it needed?

my_dict = {}
my_dict["a"] = my_dict.get("a", 0) + 1

### Large dictionary vs. generator

my_dict = {i: i**2 for i in range(10_000_000)}

def squared_numbers():
    for i in range(10_000_000):
        yield i, i**2

my_dict = dict(squared_numbers())

### setdefault vs. get

data = {}
if "name" not in data:
    data["name"] = "kiran"

data = {}
data.setdefault("name", "kiran")

name = data.setdefault("name", some_expensive_function())

name = data.get("name", "kiran")

### Counting items manually vs. using Counter

words = ["apple", "banana", "apple"]
word_count = {}
for word in words:
    word_count[word] = word_count.get(word, 0) + 1

from collections import Counter
word_count = Counter(words)

~~~
