### 🟢 **1\. What is a Byte?**

A **byte** is the smallest unit of data that a computer processes.

-   Each character (letter, number, symbol) in a file is stored as **one or more bytes**.

-   **Example:**

-   The letter `A` is stored as **1 byte** (`65` in ASCII).

-   The letter `ह` (Hindi/Nepali character) is stored as **3 bytes** (UTF-8 encoding).

-   The emoji `😊` is stored as **4 bytes**.

A is Represented as 65 because computer can only understand 0 and 1.

```py
print(len("A".encode("utf-8")))      # Output: 1
print(len("ह".encode("utf-8")))      # Output: 3
print(len("😊".encode("utf-8")))     # Output: 4
```

### 🟢 **2\. Why Do We Need to Read the Whole File?**

For counting **lines**, Python can use `\n` (newline) as a separator. It doesn't need to read the whole file at once---just one line at a time.

However, for counting **bytes**, there is **no shortcut** because:

- A file is **just a long sequence of bytes** with no automatic breakpoints.
- We don't know where the last byte is **until we read everything**.

**Example:** Imagine a file contains:

```py
Hello
World
😊
```

The **human eye** sees **3 lines**, but in memory, the file is stored as bytes:

`72 101 108 108 111 10 87 111 114 108 100 10 240 159 152 138 10`

Breaking it down:

- `"Hello"` → **5 bytes** (`72 101 108 108 111`)
- `"\n"` (newline) → **1 byte** (`10`)
- `"World"` → **5 bytes** (`87 111 114 108 100`)
- `"\n"` → **1 byte** (`10`)
- `"😊"` → **4 bytes** (`240 159 152 138`)
- `"\n"` → **1 byte** (`10`)

#### **If we only read part of the file, we might miss some bytes!**

Since bytes **don't have a built-in separator** (like `\n` for lines), the only way to count them **is to read all of them**.

### 🟢 **4\. Why Can't We Skip Bytes?**

Imagine you have a **book** and you want to count all the letters. You can:

- Count **each letter one by one**.
- Or **count the words instead** (faster, but less accurate for counting letters).

When counting **lines**, we can **skip to the next newline (`\n`)**, but when counting **bytes**, every single one matters.

---

### **Final Summary**

✅ When counting lines (`-l`), Python can read one line at a time using `\n` as a **separator**.\
✅ When counting bytes (`-c`), **there is no separator**, so we **must** read everything.\
✅ **Images, videos, and binary files** have no lines---only bytes, making full reading necessary.

This is why:

`byteCount = len(file.read())  # Reads the full file`

is needed for byte counting, but for large files, we use **chunked reading** to save memory:

```py
for chunk in iter(lambda: file.read(4096), b""):  # Read 4KB at a time
    byteCount += len(chunk)
```
