
# Working with Advanced File Manipulation and Text Processing

This course covers advanced techniques for manipulating files, processing text, and automating data workflows in Linux. Mastering these skills will allow you to efficiently handle complex file operations, extract and manipulate data, and automate report generation.

## Table of Contents
1. [Mastering File Permissions and Ownership](#mastering-file-permissions-and-ownership)
2. [File Compression and Archiving](#file-compression-and-archiving)
3. [Advanced Text Searching with grep and awk](#advanced-text-searching-with-grep-and-awk)
4. [File Parsing and Report Generation with awk](#file-parsing-and-report-generation-with-awk)
5. [Text Processing with sed](#text-processing-with-sed)
6. [Working with JSON and XML in Bash Scripts](#working-with-json-and-xml-in-bash-scripts)
7. [Regular Expressions in Detail](#regular-expressions-in-detail)
8. [Working with Large Files and Streams](#working-with-large-files-and-streams)
9. [Sorting and Filtering Data](#sorting-and-filtering-data)
10. [Parsing CSV and Log Files with Bash](#parsing-csv-and-log-files-with-bash)

## 1. Mastering File Permissions and Ownership
- **Definition**: Linux file permissions define who can read, write, or execute files. Ownership controls who can modify the permissions.
- **Example**:
  - **Change Permissions**:
    ```bash
    chmod 755 filename
    ```
  - **Change Ownership**:
    ```bash
    chown user:group filename
    ```
  - **Set ACL**:
    ```bash
    setfacl -m u:user:rw filename
    ```
- **Explanation**: `chmod` modifies permissions, `chown` changes file ownership, and `setfacl` manages Access Control Lists for more granular permissions.

## 2. File Compression and Archiving
- **Definition**: Compressing files reduces storage size, and archiving groups multiple files into one package for easier management.
- **Example**:
  - **Create a tar Archive**:
    ```bash
    tar -cvf archive.tar file1 file2
    ```
  - **Compress with gzip**:
    ```bash
    gzip file
    ```
  - **Extract a zip file**:
    ```bash
    unzip archive.zip
    ```
- **Explanation**: `tar` is used to create archives, `gzip` compresses files, and `unzip` extracts compressed zip files.

## 3. Advanced Text Searching with grep and awk
- **Definition**: `grep` is used for searching text patterns, while `awk` allows for more complex text processing and pattern matching.
- **Example**:
  - **Search with grep**:
    ```bash
    grep 'pattern' filename
    ```
  - **Advanced Search with awk**:
    ```bash
    awk '/pattern/ {print $1}' filename
    ```
- **Explanation**: `grep` searches for simple patterns, and `awk` can perform advanced data extraction and manipulation based on patterns.

## 4. File Parsing and Report Generation with awk
- **Definition**: `awk` is a powerful tool for parsing and processing text files, particularly useful for generating reports.
- **Example**:
  - **Print Specific Columns**:
    ```bash
    awk '{print $1, $3}' file.txt
    ```
  - **Sum Values in Column**:
    ```bash
    awk '{sum+=$2} END {print sum}' file.txt
    ```
- **Explanation**: `awk` splits input into fields and performs actions on them, making it ideal for report generation and analysis.

## 5. Text Processing with sed
- **Definition**: `sed` is a stream editor for transforming text in a pipeline or file, useful for text substitution, deletion, and insertion.
- **Example**:
  - **Substitute Text**:
    ```bash
    sed 's/old/new/g' file.txt
    ```
  - **Delete Line**:
    ```bash
    sed '3d' file.txt
    ```
- **Explanation**: `sed` performs text transformations like substitutions and deletions based on patterns.

## 6. Working with JSON and XML in Bash Scripts
- **Definition**: Parsing and manipulating structured data like JSON and XML is common in data processing and web service integration.
- **Example**:
  - **Parse JSON with jq**:
    ```bash
    jq '.key' file.json
    ```
  - **Parse XML with xmllint**:
    ```bash
    xmllint --xpath "//tag" file.xml
    ```
- **Explanation**: `jq` and `xmllint` are specialized tools for parsing and querying JSON and XML data respectively.

## 7. Regular Expressions in Detail
- **Definition**: Regular expressions (regex) are patterns used to match and manipulate strings based on specific rules.
- **Example**:
  - **Simple regex with grep**:
    ```bash
    grep '^abc' file.txt
    ```
  - **Advanced regex with awk**:
    ```bash
    awk '/^[0-9]{3}-[0-9]{2}-[0-9]{4}/' file.txt
    ```
- **Explanation**: Regular expressions are powerful for pattern matching, and tools like `grep` and `awk` utilize them for searching and processing text.

## 8. Working with Large Files and Streams
- **Definition**: Large files can be difficult to work with in memory, so Linux tools provide ways to process files line by line or in chunks.
- **Example**:
  - **Process Large Files with awk**:
    ```bash
    awk '{print $1}' largefile.txt
    ```
  - **Stream Output with less**:
    ```bash
    cat largefile.txt | less
    ```
- **Explanation**: `awk` processes large files efficiently, and `less` allows viewing large files interactively without loading them fully into memory.

## 9. Sorting and Filtering Data
- **Definition**: Sorting and filtering data is essential for organizing and analyzing large datasets.
- **Example**:
  - **Sort Data**:
    ```bash
    sort file.txt
    ```
  - **Remove Duplicates**:
    ```bash
    uniq file.txt
    ```
  - **Cut Columns from Data**:
    ```bash
    cut -d',' -f1 file.csv
    ```
- **Explanation**: `sort` organizes data, `uniq` removes duplicate lines, and `cut` extracts specific columns from files.

## 10. Parsing CSV and Log Files with Bash
- **Definition**: Parsing CSV and log files is critical for extracting meaningful information from structured data.
- **Example**:
  - **Parse CSV**:
    ```bash
    awk -F',' '{print $1, $2}' file.csv
    ```
  - **Extract Logs for Errors**:
    ```bash
    grep 'ERROR' /var/log/syslog
    ```
- **Explanation**: `awk` is used to parse CSV by specifying a delimiter, and `grep` helps filter logs for specific patterns like errors.

## Conclusion

### Key Takeaways:
1. Mastering file permissions and ownership is critical for managing security and access control.
2. Tools like `tar`, `gzip`, and `zip` are essential for compressing and archiving files, while `unzip` extracts them.
3. Advanced text processing with `grep`, `awk`, and `sed` allows for efficient manipulation and extraction of data from files.
4. Regular expressions are an essential tool for pattern matching and string manipulation.
5. Tools like `jq` and `xmllint` help parse and manipulate structured data formats like JSON and XML.

### Practical Exercise:
1. Write a script that parses a CSV file, calculates the total of a specific column, and outputs the result.
2. Use `awk` to generate a report summarizing the number of occurrences of each word in a log file.
3. Compress a directory into a `.tar.gz` archive and extract it to a different location.
4. Create a `sed` command to find and replace all instances of "foo" with "bar" in a text file.
5. Write a bash script that processes a large log file and extracts all unique IP addresses. 
