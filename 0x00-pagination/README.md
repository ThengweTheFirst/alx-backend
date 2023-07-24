## 0x00. Pagination

Welcome to the Pagination project! This project focuses on Back-end concepts and aims to teach you various techniques for paginating datasets in a deletion-resilient manner using Python.

### Learning Objectives

By the end of this project, you will be able to explain the following concepts to anyone without the help of Google:

1. How to paginate a dataset with simple `page` and `page_size` parameters.
2. How to paginate a dataset with hypermedia metadata.
3. How to paginate in a deletion-resilient manner.

### Requirements

- All your files will be interpreted/compiled on Ubuntu 18.04 LTS using Python 3 (version 3.7).
- All your files should end with a new line.
- The first line of all your files should be exactly `#!/usr/bin/env python3`.
- A `README.md` file, at the root of the folder of the project, is mandatory.
- Your code should use the `pycodestyle` style (version 2.5.*).
- The length of your files will be tested using `wc`.
- All your modules should have documentation (`python3 -c 'print(__import__("my_module").__doc__)'`).
- All your functions should have documentation (`python3 -c 'print(__import__("my_module").my_function.__doc__)'`).
- A documentation is not just a simple word; it's a real sentence explaining the purpose of the module, class, or method (the length of it will be verified).
- All your functions and coroutines must be type-annotated.

### Tasks

#### Task 0: Simple helper function

Write a function named `index_range` that takes two integer arguments `page` and `page_size`.

The function should return a tuple of size two containing a start index and an end index corresponding to the range of indexes to return in a list for those particular pagination parameters.

Page numbers are 1-indexed, i.e., the first page is page 1.

**Sample Usage:**

```python
index_range(1, 7)  # Output: (0, 7)
index_range(page=3, page_size=15)  # Output: (30, 45)
```

#### Task 1: Simple pagination

Implement a method named `get_page` in the `Server` class that takes two integer arguments `page` with a default value of 1 and `page_size` with a default value of 10.

You have to use the provided CSV file "Popular_Baby_Names.csv".

Use `assert` to verify that both arguments are integers greater than 0.
Use `index_range` to find the correct indexes to paginate the dataset correctly and return the appropriate page of the dataset (i.e., the correct list of rows).
If the input arguments are out of range for the dataset, an empty list should be returned.

**Sample Usage:**

```python
server = Server()

# Positive test cases
print(server.get_page(1, 3))
print(server.get_page(3, 2))
print(server.get_page(3000, 100))

# Negative test cases
try:
    should_err = server.get_page(-10, 2)
except AssertionError:
    print("AssertionError raised with negative values")

try:
    should_err = server.get_page(0, 0)
except AssertionError:
    print("AssertionError raised with 0")

try:
    should_err = server.get_page(2, 'Bob')
except AssertionError:
    print("AssertionError raised when page and/or page_size are not ints")
```

#### Task 2: Hypermedia pagination

Implement a method named `get_hyper` in the `Server` class that takes the same arguments (and defaults) as `get_page` and returns a dictionary containing the following key-value pairs:

- `page_size`: the length of the returned dataset page.
- `page`: the current page number.
- `data`: the dataset page (equivalent to the return from the previous task).
- `next_page`: the number of the next page, `None` if no next page.
- `prev_page`: the number of the previous page, `None` if no previous page.
- `total_pages`: the total number of pages in the dataset as an integer.

Make sure to reuse `get_page` in your implementation.

**Sample Usage:**

```python
server = Server()

print(server.get_hyper(1, 2))
print(server.get_hyper(2, 2))
print(server.get_hyper(100, 3))
print(server.get_hyper(3000, 100))
```

#### Task 3: Deletion-resilient hypermedia pagination

Implement a method named `get_hyper_index` in the `Server` class with two integer arguments: `index` with a default value of `None` and `page_size` with a default value of 10.

The method should return a dictionary with the following key-value pairs:

- `index`: the current start index of the return page. That is the index of the first item in the current page. For example, if requesting page 3 with `page_size` 20, and no data was removed from the dataset, the current index should be 60.
- `next_index`: the next index to query with. That should be the index of the first item after the last item on the current page.
- `page_size`: the current page size.
- `data`: the actual page of the dataset.

Requirements/Behavior:

- Use `assert` to verify that `index` is in a valid range.
- If the user queries index 0, `page_size` 10, they will get rows indexed 0 to 9 included.
- If they request the next index (10) with `page_size` 10, but rows 3, 6, and 7 were deleted, the user should still receive rows indexed 10 to 19 included.

**Sample Usage:**

```python
server = Server()
server.indexed_dataset()

try:
    server.get_hyper_index(300000, 100)
except AssertionError:
    print("AssertionError raised when out of range")

index = 3
page_size = 2

print("Nb items: {}".format(len(server._Server__indexed_dataset)))

# 1- request first index
res = server.get_hyper_index(index, page_size)
print(res)

# 2- request next index
print(server.get_hyper_index(res.get('next_index'), page_size))

# 3- remove the first index
del server._Server__indexed_dataset[res.get('index')]
print("Nb items: {}".format(len(server._Server__indexed_dataset)))

# 4- request again the initial index -> the first data retrieved is not the same as the first request
print(server.get_hyper_index(index, page_size))

# 5- request again initial next index -> same data page as the request 2-
print(server.get_hyper_index(res.get('next_index'), page_size))
```

