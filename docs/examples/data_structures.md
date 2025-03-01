# Data

## Data Structures

Introduction of  python data structures like lists, dictionaries, and dataframes.

---


### 1. Lists

Lists are used to store multiple items in a single variable.

Creating a List

```python
fruits = ["apple", "banana", "cherry"]
print(fruits)
```

Accessing Items

```python
print(fruits[0])  # First item
print(fruits[-1])  # Last item
```

Modifying Lists

```python
fruits.append("orange")  # Add an item
fruits[1] = "blueberry"  # Change an item
print(fruits)
```

Iterating Through a List

```python
for fruit in fruits:
    print(fruit)
```

Common List Methods

- `append(item)`: Add an item
- `remove(item)`: Remove an item
- `len(list)`: Get the number of items
- `sort()`: Sort the list

Exercise:

1. Create a list of your favorite hobbies.
2. Add a new hobby to the list.
3. Print each hobby using a loop.

---

### 2. Dictionaries

Dictionaries store data in key-value pairs.

  Creating a Dictionary

```python
student = {"name": "Alex", "age": 16, "grade": "A"}
print(student)
```

  Accessing Items

```python
print(student["name"])  # Access value by key
```

  Adding/Updating Keys

```python
student["school"] = "High School"  # Add a new key
student["grade"] = "A+"  # Update value
print(student)
```

  Iterating Through a Dictionary

```python
for key, value in student.items():
    print(key, ":", value)
```

  Common Dictionary Methods

- `keys()`: Get all keys
- `values()`: Get all values
- `items()`: Get all key-value pairs

  Exercise:

1. Create a dictionary with details about your favorite book (title, author, year).
2. Add a new key for the genre.
3. Print all the keys and values.

---

### 3. DataFrames (Using pandas)

 What is a DataFrame?
A DataFrame is a 2-dimensional table-like data structure in the pandas library. Think of it as a spreadsheet.

  Setting Up pandas
Make sure you have pandas installed:

```bash
pip install pandas
```

  Creating a DataFrame

```python
import pandas as pd

data = {
    "Name": ["Alice", "Bob", "Charlie"],
    "Age": [16, 17, 16],
    "Grade": ["A", "B", "A"]
}

df = pd.DataFrame(data)
print(df)
```

  Accessing Columns

```python
print(df["Name"])  # Access a single column
print(df[["Name", "Age"]])  # Access multiple columns
```

  Filtering Rows

```python
print(df[df["Age"] > 16])  # Students older than 16
```

  Adding a New Column

```python
df["Passed"] = [True, False, True]
print(df)
```

  Iterating Through Rows

```python
for index, row in df.iterrows():
    print(row["Name"], "is", row["Age"], "years old.")
```

  Exercise:

1. Create a DataFrame with data about your favorite movies (columns: Title, Year, Genre).
2. Add a new column for Rating.
3. Filter the movies to show only those released after 2010.

---

### 4. Comparing Lists, Dictionaries, and DataFrames

| Feature            | List                     | Dictionary               | DataFrame             |
|---------------------|--------------------------|--------------------------|-----------------------|
| Data Organization   | Ordered, items by index | Key-value pairs          | Rows and columns      |
| Access Method       | By index                | By key                   | By row/column         |
| Ideal Use Case      | Simple collections      | Mapping relationships    | Tabular data          |

---

### 5. Final Project Idea: Student Report System

Build a system that:

1. Stores student data in a DataFrame.
2. Allows adding a new student (Name, Age, Grade).
3. Filters students by a minimum grade.
4. Prints all student data.

 Example Code for the System:

```python
import pandas as pd

# Initial data
data = {
    "Name": ["Alice", "Bob", "Charlie"],
    "Age": [16, 17, 16],
    "Grade": ["A", "B", "A"]
}
df = pd.DataFrame(data)

# Add a new student
new_student = {"Name": "Daisy", "Age": 17, "Grade": "A+"}
df = df.append(new_student, ignore_index=True)

# Filter by grade
print("Students with grade A or higher:")
print(df[df["Grade"] >= "A"])
```

