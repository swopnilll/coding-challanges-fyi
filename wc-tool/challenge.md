### **Challenge Breakdown: Build Your Own `wc` Tool**

The challenge is to recreate the Unix `wc` (word count) tool from scratch, adhering to the Unix Philosophy of simplicity and composability. You'll build a CLI tool called `ccwc` that progressively implements core functionality through six steps, handling file/input analysis and supporting multiple counting modes.

---

### **Functional Requirements**

1.  **Step Zero**: Setup environment and test file.

2.  **Step One** (`-c`): Count bytes in a file.

3.  **Step Two** (`-l`): Count lines in a file.

4.  **Step Three** (`-w`): Count words in a file.

5.  **Step Four** (`-m`): Count characters (locale-dependent).

6.  **Step Five** (default): Output lines, words, and bytes.

7.  **Final Step**: Read from standard input (stdin) if no file is provided.

---

### **Key Technical Components**

1.  **Byte Counting**:

    - Read files in binary mode or use filesystem metadata.

    - Handle stdin by reading raw bytes.

2.  **Line Counting**:

    - Detect newline characters (`\n`).

    - Works for both files and piped input.

3.  **Word Counting**:

    - Split text into tokens separated by whitespace (spaces, tabs, newlines).

    - Handle edge cases (e.g., multiple spaces, empty lines).

4.  **Character Counting**:

    - Decode input using system locale (e.g., UTF-8 for multibyte chars).

    - Fallback to byte count if locale doesn't support multibyte.

5.  **Argument Parsing**:

    - Support flags `-c`, `-l`, `-w`, `-m`.

    - Default to `-c -l -w` when no flags are given.

6.  **Input Handling**:

    - Read from files or stdin (pipes/redirects).

    - Format output with right-aligned numbers and optional filename.

---

### **Prerequisites**

1.  **Programming Basics**:

    - File I/O (reading files, handling stdin).

    - String manipulation (splitting words, counting lines).

2.  **Command-Line Skills**:

    - Parsing CLI arguments (e.g., Python's `argparse`, Go's `flag`).

    - Handling pipes (`|`) and input redirection.

3.  **Understanding of Encodings**:

    - Difference between bytes vs. characters (ASCII vs. Unicode).

    - Locale settings (how `-m` depends on system configuration).

4.  **Unix Tool Behavior**:

    - Study `man wc` to replicate output formatting.

    - Test edge cases (empty files, multibyte chars).
