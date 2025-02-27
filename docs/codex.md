# Code Examples

## Data Structures

Here’s a tutorial introducing Python data structures like lists, dictionaries, and dataframes in a simple way suitable for high school students.

---

## Data Structures in Python

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

## File IO

Here’s a tutorial on writing, saving, and reading files in Python, along with template functions for working with plain text, CSV, and JSON files.

---

## 1. Plain Text File

Plain text files are the simplest type of file. You can write strings to them or read their content as text.

### Template Function for Plain Text Files

 Writing to a Plain Text File

```python
def write_to_text_file(file_path, text):
    with open(file_path, 'w') as file:  # Open file in write mode
        file.write(text)  # Write text to the file
```

 Reading from a Plain Text File

```python
def read_from_text_file(file_path):
    with open(file_path, 'r') as file:  # Open file in read mode
        return file.read()  # Return the content of the file
```

 Example Usage

```python
write_to_text_file('example.txt', 'Hello, World!')
content = read_from_text_file('example.txt')
print(content)
```

---

## 2. CSV File

CSV (Comma-Separated Values) files are used to store tabular data.

### Template Function for CSV Files

 Writing to a CSV File

```python
import csv

def write_to_csv(file_path, data):
    with open(file_path, 'w', newline='') as file:  # Open file in write mode
        writer = csv.writer(file)
        writer.writerows(data)  # Write rows of data
```

 Reading from a CSV File

```python
def read_from_csv(file_path):
    with open(file_path, 'r') as file:  # Open file in read mode
        reader = csv.reader(file)
        return list(reader)  # Convert rows to a list
```

 Example Usage

```python
data = [
    ['Name', 'Age', 'Grade'],
    ['Alice', 16, 'A'],
    ['Bob', 17, 'B']
]
write_to_csv('students.csv', data)

content = read_from_csv('students.csv')
for row in content:
    print(row)
```

---

## 3. JSON File

JSON (JavaScript Object Notation) is used to store structured data, such as dictionaries or lists.

### Template Function for JSON Files

 Writing to a JSON File

```python
import json

def write_to_json(file_path, data):
    with open(file_path, 'w') as file:  # Open file in write mode
        json.dump(data, file, indent=4)  # Write data to the file in JSON format
```

 Reading from a JSON File

```python
def read_from_json(file_path):
    with open(file_path, 'r') as file:  # Open file in read mode
        return json.load(file)  # Load data from JSON file
```

 Example Usage

```python
data = {
    'students': [
        {'name': 'Alice', 'age': 16, 'grade': 'A'},
        {'name': 'Bob', 'age': 17, 'grade': 'B'}
    ]
}
write_to_json('students.json', data)

content = read_from_json('students.json')
print(content)
```

---

### Summary of File Types

| File Type | Python Module | Best for                          |
|-----------|---------------|------------------------------------|
| Plain Text| `open()`       | Storing simple text or logs       |
| CSV       | `csv`          | Tabular data                     |
| JSON      | `json`         | Structured data (hierarchical)   |

Each of these functions can be adapted based on specific requirements. Let me know if you'd like further customizations or examples!
