
---

# `grep` Command - Detailed Guide

## Overview

The `grep` command in Linux and Unix-like systems is a powerful tool used for searching and filtering text. It searches through files (or input) for lines that match a given pattern, and it outputs those matching lines. The name `grep` stands for **Global Regular Expression Print**, reflecting its ability to use regular expressions (regex) for matching patterns.

## Syntax

```bash
grep [OPTIONS] PATTERN [FILE...]
```

- **PATTERN**: The text pattern or regular expression to search for.
- **FILE**: One or more files to search within. If no file is specified, `grep` reads from the standard input.
- **OPTIONS**: Various options to modify the behavior of the search.

## Basic Usage

```bash
grep "pattern" file.txt
```

This command will search for the exact string "pattern" in `file.txt` and display all matching lines.

## Common Options

### 1. `-i` (Case-insensitive search)

Search for the pattern without considering case sensitivity.

```bash
grep -i "pattern" file.txt
```

### 2. `-v` (Invert match)

Show lines that do **not** match the pattern.

```bash
grep -v "pattern" file.txt
```

### 3. `-r` or `-R` (Recursive search)

Search recursively in directories and their subdirectories.

```bash
grep -r "pattern" /path/to/directory
```

### 4. `-l` (List file names)

Show only the names of files that contain the pattern, rather than the matching lines.

```bash
grep -l "pattern" *.txt
```

### 5. `-n` (Line numbers)

Show the line numbers of matching lines in the output.

```bash
grep -n "pattern" file.txt
```

### 6. `-w` (Word match)

Search for the pattern as a whole word (i.e., match the entire word, not just a substring).

```bash
grep -w "pattern" file.txt
```

### 7. `-c` (Count matches)

Count the number of lines that match the pattern.

```bash
grep -c "pattern" file.txt
```

### 8. `-h` (Suppress filename)

Suppress the file name in the output (useful when searching multiple files).

```bash
grep -h "pattern" *.txt
```

### 9. `-o` (Only matching part)

Print only the part of the line that matches the pattern, rather than the whole line.

```bash
grep -o "pattern" file.txt
```

### 10. `-A NUM` (Show lines after match)

Show **NUM** lines after the matching line(s).

```bash
grep -A 3 "pattern" file.txt
```

### 11. `-B NUM` (Show lines before match)

Show **NUM** lines before the matching line(s).

```bash
grep -B 2 "pattern" file.txt
```

### 12. `-C NUM` (Show context)

Show **NUM** lines before and after the match, providing context.

```bash
grep -C 2 "pattern" file.txt
```

### 13. `-E` (Extended regex)

Treat the pattern as an **extended regular expression** (ERE). This allows more complex patterns (such as using `+`, `?`, `|`, etc.).

```bash
grep -E "pattern1|pattern2" file.txt
```



## Regular Expressions in `grep`

`grep` supports regular expressions (regex), which provide powerful pattern matching. Regular expressions allow for more complex and flexible searches. Some basic regex patterns include:

- `.`: Matches any single character.
- `*`: Matches zero or more of the preceding element.
- `^`: Anchors the match to the start of the line.
- `$`: Anchors the match to the end of the line.
- `[]`: Matches any one of the characters inside the square brackets.
- `|`: Matches either the expression on the left or the one on the right.


