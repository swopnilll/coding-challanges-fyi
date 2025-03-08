# Binary Mode (`"rb"`) vs Text Mode (`"r"`)

When you open a file in Python, you can choose to read it in **binary mode** or **text mode**. Here's the difference:

---

## 1. Return Type

- **Binary Mode (`"rb"`)**:

  - Returns raw data as a `bytes` object.
  - Example: `b'\x48\x65\x6c\x6c\x6f'` (this is the raw byte representation of "Hello").

- **Text Mode (`"r"`)**:
  - Returns the data as a `str` object (a string of text).
  - Example: `"Hello"` (this is the actual text you can read).

---

## 2. Memory Contents

- **Binary Mode (`"rb"`)**:

  - Reads the file **exactly as it is stored** on disk.
  - Each byte (8 bits) is treated as a number between 0 and 255.
  - No interpretation or conversion is done.

- **Text Mode (`"r"`)**:
  - Reads the file as **text**.
  - Converts the raw bytes into characters using an **encoding** (like UTF-8 or ASCII).
  - Example: The byte `0x48` becomes the character `'H'`.

---

## 3. Newline Handling

- **Binary Mode (`"rb"`)**:

  - Does **not change** any data in the file.
  - If the file has `\r\n` (Windows-style line endings), it stays as `\r\n`.
  - If the file has `\n` (Unix-style line endings), it stays as `\n`.

- **Text Mode (`"r"`)**:
  - Automatically **converts line endings** to `\n` (Unix-style).
  - On Windows, `\r\n` is converted to `\n`.
  - On Unix, `\n` stays as `\n`.

---

## 4. Encoding

- **Binary Mode (`"rb"`)**:

  - Does **not use encoding**.
  - You get the raw bytes, exactly as they are stored on disk.

- **Text Mode (`"r"`)**:
  - Uses an **encoding** (like UTF-8, ASCII, etc.) to convert bytes into text.
  - If the file contains bytes that don't match the encoding, you might get an error (e.g., `UnicodeDecodeError`).

---

## Example

Let's say you have a file called `example.txt` with the following content:

```
Hello
World
```

### **Binary Mode (`"rb"`)**:

```python
with open("example.txt", "rb") as file:
    content = file.read()
print(content)
```

#### **Output:**

```
b'Hello\r\nWorld'
```

- The `b` at the beginning means it's a `bytes` object.
- `\r\n` is preserved as raw bytes (Windows line ending).

### **Text Mode (`"r"`)**:

```python
with open("example.txt", "r") as file:
    content = file.read()
print(content)
```

#### **Output:**

```
Hello
World
```

- The `\r\n` is converted to `\n` (Unix-style line ending).
- The result is a readable string.

---

## When to Use Which?

- Use **Binary Mode (`"rb"`)** when:

  - You're working with non-text files (e.g., images, videos, executables).
  - You need the raw bytes without any conversion.

- Use **Text Mode (`"r"`)** when:
  - You're working with text files (e.g., `.txt`, `.csv`, `.json`).
  - You want Python to handle encoding and line endings for you.

---

## Summary

- **Binary Mode** gives you the raw bytes, exactly as they are stored on disk.
- **Text Mode** converts the bytes into readable text, handling encoding and line endings for you.
