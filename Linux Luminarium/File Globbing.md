# Challenge 5: File Globbing

## Course Introduction
In this challenge, you will learn how to use file globbing to match file names and paths in Linux. File globbing allows you to use wildcards to create flexible patterns for searching files. Your goal is to obtain the flag by mastering these techniques.

## Obtaining the Flag
To successfully obtain the flag for this challenge, follow these methods based on the concepts discussed:

### Method 1: Matching with `*`
- **Description**: The `*` wildcard matches any number of characters in file names.
- **Example**:
    ```bash
    # Command to find files
    ls *.txt
    ```
- **Flag Retrieval**: Use the command to locate the flag.

### Method 2: Matching with `?`
- **Description**: The `?` wildcard matches a single character in a file name.
- **Example**:
    ```bash
    # Command to find files
    ls file?.txt
    ```
- **Flag Retrieval**: Identify the flag using this pattern.

### Method 3: Matching with `[]`
- **Description**: Square brackets allow you to specify a set of characters to match.
- **Example**:
    ```bash
    # Command to find files
    ls file[1-3].txt
    ```
- **Flag Retrieval**: Apply this method to uncover the flag.

### Method 4: Matching paths with `[]`
- **Description**: Use brackets to match directories or paths.
- **Example**:
    ```bash
    # Command to find directories
    ls /home/user/[a-z]*/
    ```
- **Flag Retrieval**: Find the flag hidden in the specified path.

### Method 5: Mixing Globs
- **Description**: Combine different wildcards for complex searches.
- **Example**:
    ```bash
    # Command to find files
    ls file*.[ch]
    ```
- **Flag Retrieval**: Use this mixed approach to locate the flag.

### Method 6: Exclusionary Globbing
- **Description**: Exclude certain patterns using the `!` operator.
- **Example**:
    ```bash
    # Command to exclude files
    ls !(*.tmp)
    ```
- **Flag Retrieval**: Exclude unnecessary files and find the flag.

## Conclusion
Once you have practiced with these methods, you should be able to successfully retrieve the flag using file globbing techniques. Good luck!
