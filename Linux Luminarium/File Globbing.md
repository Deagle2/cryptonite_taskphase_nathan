# Challenge 5: File Globbing

## Course Introduction
Globbing lets you reference files without typing them all out, or typing out their full paths. File globbing allows you to use wildcards to create flexible patterns for searching files.

### Matching with `*`
- **Description**: The `*` wildcard matches any number of characters in file names.
- **Example**:
    ```bash
    # Command to find files
    ls *.txt
    ```
- **Flag Retrieval**: Use the command to locate the flag.

### Matching with `?`
- **Description**: The `?` wildcard matches a single character in a file name.
- **Example**:
    ```bash
    # Command to find files
    ls file?.txt
    ```
- **Flag Retrieval**: Identify the flag using this pattern.

###  Matching with `[]`
- **Description**: Square brackets allow you to specify a set of characters to match.
- **Example**:
    ```bash
    # Command to find files
    ls file[1-3].txt
    ```
- **Flag Retrieval**: Apply this method to uncover the flag.

### Matching paths with `[]`
- **Description**: Use brackets to match directories or paths.
- **Example**:
    ```bash
    # Command to find directories
    ls /home/user/[a-z]*/
    ```
- **Flag Retrieval**: Find the flag hidden in the specified path.

### Mixing Globs
- **Description**: Combine different wildcards for complex searches.
- **Example**:
    ```bash
    # Command to find files
    ls file*.[ch]
    ```
- **Flag Retrieval**: Use this mixed approach to locate the flag.

### Exclusionary Globbing
- **Description**: Exclude certain patterns using the `!` operator.
- **Example**:
    ```bash
    # Command to exclude files
    ls !(*.tmp)
    ```
- **Flag Retrieval**: Exclude unnecessary files and find the flag.

## Conclusion
Once you have practiced with these methods, you should be able to successfully retrieve the flag using file globbing techniques. Good luck!
