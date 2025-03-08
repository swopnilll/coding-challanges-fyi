### Solution

1.  **Import the sys Module:**\
    At the start of your script, import the `sys` module. This module gives you access to `sys.argv`, which is a list of all the command-line arguments.

2.  **Accessing Command-Line Arguments:**

    - `sys.argv[0]` is the name of the script (e.g., `ccwc` or `ccwc.py`).
    - `sys.argv[1]` should be the option (in this case, `-c`).
    - `sys.argv[2]` should be the filename (e.g., `test.txt`).

3.  **Validating Arguments:**\
    Check if the expected number of arguments is provided. This helps avoid errors if the user doesn't pass the correct arguments.

4.  **Opening the File:**\
    We can use Python's built-in `open()` function to read the file. Since we need to count the bytes, we can open the file in binary mode (`"rb"`). This ensures that we get the raw bytes, which is useful for an accurate byte count.

5.  **Reading and Counting Bytes:**\
    Read the file content into a variable and use the `len()` function to count the total number of bytes.

6.  **Output the Result:**\
    Finally, print out the byte count along with the filename.
