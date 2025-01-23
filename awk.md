
---

# `awk` Command - Detailed Guide

## Overview

`awk` is a powerful text processing tool in Unix and Linux systems. It's used to process and analyze text files, especially those structured in rows and columns (e.g., CSV, log files, etc.). `awk` allows you to perform a wide range of operations such as searching, replacing, extracting, and formatting text, all based on patterns or conditions.

### Basic Syntax

```bash
awk 'pattern {action}' file
```

- **`pattern`**: A condition or pattern that selects lines from the input.
- **`action`**: What to do when the pattern matches. Actions are written within `{}`.
- **`file`**: The file you want to process (optional if you're reading from standard input).

If no `pattern` is provided, `awk` performs the `action` on all lines. If no `action` is specified, `awk` will print the lines that match the `pattern`.

### **Important Built-in Variables in `awk`:**
- **`$0`**: Represents the entire current line.
- **`$1, $2, ..., $n`**: Represents specific fields in the current line (e.g., `$1` is the first field, `$2` is the second, and so on).

### Basic Examples:

1. **Print the entire line:**
   ```bash
   awk '{print $0}' file.txt
   ```
   This prints every line from `file.txt`. `$0` represents the entire line.

2. **Print specific columns (fields):**
   ```bash
   awk '{print $1, $3}' file.txt
   ```
   This prints the first and third fields of each line. You can use `$1`, `$2`, etc., to access specific fields.

3. **Print the number of fields in each line:**
   ```bash
   awk '{print NF}' file.txt
   ```
   This prints the number of fields (columns) in each line.

4. **Print lines matching a pattern:**
   ```bash
   awk '/pattern/ {print $0}' file.txt
   ```
   This will print all lines that contain the word "pattern".

5. **Use conditions (only print lines where field 2 is greater than 10):**
   ```bash
   awk '$2 > 10 {print $0}' file.txt
   ```
   This prints lines where the second field has a value greater than 10.

6. **Perform arithmetic operations on fields:**
   ```bash
   awk '{print $1 + $2}' file.txt
   ```
   This adds the first and second fields of each line and prints the result.

---

### Real-World Use Cases for `awk`:

1. **Extracting specific fields from a CSV file:**
   Let's say you have a CSV file `data.csv` with the following content:

   ```csv
   name,age,location
   Alice,30,New York
   Bob,25,San Francisco
   Carol,28,Boston
   ```

   If you want to extract the names and ages (fields 1 and 2) from the CSV:

   ```bash
   awk -F',' '{print $1, $2}' data.csv
   ```

   Output:
   ```
   name age
   Alice 30
   Bob 25
   Carol 28
   ```

   Here, the `-F','` option sets the field separator to a comma, which is typical in CSV files.

2. **Filtering log files by a certain pattern:**
   If you're analyzing a log file and want to print all lines where the status code is `200`:

   ```bash
   awk '$9 == 200 {print $0}' access.log
   ```

   In this example, `$9` refers to the status code field in an Apache access log (assuming common log format).

3. **Summing numbers from a column:**
   Suppose you have a file `numbers.txt` with a column of numbers, and you want to calculate the sum:

   ```bash
   awk '{sum += $1} END {print sum}' numbers.txt
   ```

   This will add up all the values in the first column and print the total. The `END` block ensures the summation occurs after processing all lines.

4. **Formatting output:**
   You can format the output using `awk`'s built-in variables and string manipulation:

   ```bash
   awk '{printf "Name: %-10s Age: %-3s\n", $1, $2}' data.txt
   ```

   This prints the name and age in a formatted manner with left-aligned text.

5. **Count occurrences of a pattern:**
   To count the occurrences of a specific pattern, you can use the following:

   ```bash
   awk '/pattern/ {count++} END {print count}' file.txt
   ```

   This will search for "pattern" in the file and count how many times it appears.

---

### Using `awk` in a Pipeline Execution

`awk` is often used in combination with other commands in a pipeline to process and transform data efficiently. Here's how it fits into real-world pipeline scenarios:

1. **Get disk usage and filter the result using `awk`:**

   ```bash
   df -h | awk '$5 > 80 {print $1, $5}'
   ```

   - This command checks the disk usage (`df -h`) and prints only the file systems where usage is greater than 80%.

2. **Combining `ps` and `awk` to monitor processes:**

   ```bash
   ps aux | awk '$3 > 50 {print $1, $3, $11}'
   ```

   - This pipeline checks the processes with CPU usage greater than 50% and prints the username, CPU usage, and the command name.


---
Using tee to Save and Display Output

If you want to see the changes on the screen and save them to a file, you can use tee.
Example:
```bash
awk 'sub("fruit", "produce", $2) {print}' data.txt | tee output.txt
```
This will output the modified content to both the terminal and output.txt.