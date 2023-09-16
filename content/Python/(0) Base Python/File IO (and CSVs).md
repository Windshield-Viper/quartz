File IO allows you to read files. 

- The `input` and `print` statements already write to standard input and output.

## Opening and Closing Files
- Files have to be opened before they can be read or written to. At the end of the program, they must be closed.

### Open
`file object = open(file_name [, access_mode][, buffering])`

- Doing this creates a **file** object.
- Parameter details:
	- **file_name** − The file_name argument is a string value that contains the name of the file that you want to access.
	- **access_mode** − The access_mode determines the mode in which the file has to be opened, i.e., read, write, append, etc. This is an optional parameter and the default file access mode is read (r). Main types of access modes are listed below.
		1. **Read Only ('r’):** This mode opens the text files for reading only. The start of the file is where the handle is located. It raises the I/O error if the file does not exist. This is the default mode for opening files as well.
		2. **Read and Write ('r+’):** This method opens the file for both reading and writing. The start of the file is where the handle is located. If the file does not exist, an I/O error gets raised.
		3. **Write Only ('w’):** This mode opens the file for writing only. The data in existing files are modified and overwritten. The start of the file is where the handle is located. If the file does not already exist in the folder, a new one gets created.
		4. **Write and Read ('w+’)**: This mode opens the file for both reading and writing. The text is overwritten and deleted from an existing file. The start of the file is where the handle is located.
		5. **Append Only ('a’)**: This mode allows the file to be opened for writing. If the file doesn't yet exist, a new one gets created. The handle is set at the end of the file. The newly written data will be added at the end, following the previously written data.
		6. **Append and Read (‘a+’):** Using this method, you can read and write in the file. If the file doesn't already exist, one gets created. The handle is set at the end of the file. The newly written text will be added at the end, following the previously written data.
	- **buffering** 
		- If the buffering value is set to 0, no buffering takes place. If the buffering value is 1, line buffering is performed while accessing a file. If you specify the buffering value as an integer greater than 1, then buffering action is performed with the indicated buffer size. If negative, the buffer size is the system default(default behavior).
	- **examples**
		- `file = open("names.txt", "w")`

### Close
`fileObject.close()`

- Flushes unwritten information and closes the file object. It’s good practice to use the `close()` method to close a file.

## Reading and Writing Files

### The **write()** method
`fileObject.write(string)`

- Does not add a newline to the end of the string
- Python strings can have binary data, not just text.
- **examples**
	- `file.write(f"{name}\n")`

### The **read** method
`fileObject.read([count])`
- `count` is the number of bytes to be read from the opened file.
- if no `count` is specified then it tried to 

### The **with** keyword
- Allows you to not have to close things.
- Example below

## Example putting it all together
```python
with open("names.txt", "r") as file:
    for line in file:
        print("hello,", line.rstrip())
```

## Working with CSVs
- Use the **CSV** library
	- The library is built-in
- To read the file, use the built-in **reader**.
- A `reader` works in a `for` loop, where each iteration the `reader` gives us another row from our CSV file. 
	- This row itself is a list, where each value in the list corresponds to an element in that row. 
	- `row[0]`, for example, is the first element of the given row, while `row[1]` is the second element.
```python
import csv

students = []

with open("students.csv") as file:
    reader = csv.reader(file)
    for row in reader:
        students.append({"name": row[0], "home": row[1]})

for student in sorted(students, key=lambda student: student["name"]):
    print(f"{student['name']} is from {student['home']}")
```
- There is also **DictReader** which returns dictionaries rather than lists.
- There are also **Writers**.

[Python’s CSV Documentation](https://docs.python.org/3/library/csv.html)