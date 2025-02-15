# Automated IP Allow List Updater

## Project Description

This project automates the process of updating an IP allow list by removing unauthorized IP addresses. It’s especially useful for organizations that need to maintain restricted content access. The algorithm reads from an allow list file and a remove list, iterates through both, and updates the allow list by removing IP addresses in the remove list.

## Features

- **Automated Allow List Management**: Automatically removes unauthorized IP addresses from the allow list based on a given remove list.
- **File Handling**: Efficiently reads, processes, and writes IP addresses to manage access control.
- **Simple, Scalable Solution**: Adaptable to different organizational needs for file-based IP management.

## Project Structure

- **allow_list.txt** - Contains the IP addresses allowed access to restricted content.
- **remove_list.txt** - Lists IP addresses that should be removed from the allow list.
- **update_script.py** - Python script implementing the algorithm to update the allow list.

## How It Works

1. **Opening the File with Allow List**: Assigns `allow_list.txt` to `import_file` and uses the `with` statement to open it in read mode.
2. **Read File Contents**: Reads the content of `allow_list.txt` as a single string and stores it in a variable named `ip_addresses`.
3. **Convert String into List**: Converts the IP addresses from a string format to a list format using `.split()`.
4. **Iterate Through the Remove List**: Iterates over each IP in `remove_list.txt` to identify any matching entries in the allow list.
5. **Remove IP Addresses from Allow List**: If an IP from the remove list is found in the allow list, it is removed using `.remove()`.
6. **Update with Revised IP**: Converts the updated list of IP addresses back to a string, separating each IP by a newline, and writes it back to `allow_list.txt`.

## Code Overview

```python
# Step 1: Open the allow list file
import_file = "allow_list.txt"
with open(import_file, "r") as file:

# Step 2: Read the file contents
with open(import_file, "r") as file:
    ip_addresses = file.read()

# Step 3: Convert string to list
ip_addresses = ip_addresses.split()

# Step 4: Iterate through the remove list
with open("remove_list.txt", "r") as remove_file:
    for element in remove_file:
   
# Step 5: Remove IP addresses in remove list from allow list
        if element in ip_addresses:
            ip_addresses.remove(element)

# Step 6: Update the file with the revised IP addresses
ip_addresses = "\n".join(ip_addresses)
with open(import_file, "w") as file:
    file.write(ip_addresses)
```

## Screenshots

1. **Open the file that contains the allow list**:  
   ![Open the file that contains the allow list](Screenshots/Opening_File_with_Allow_List.png)

2. **Read the file contents**:  
   ![Read the file contents](Screenshots/Read_File_Contents.png)

3. **Convert the string into a list**:  
   ![Convert the string into a list](Screenshots/Converting_String_into_List.png)

4. **Iterate through the remove list**:  
   ![Iterate through the remove list](Screenshots/Iterating_Through_Remove_List.png)

5. **Remove IP addresses that are on the remove list**:  
   ![Remove IP addresses that are on the remove list](Screenshots/Removing_IP_Addresses.png)

6. **Update the file with the revised list of IP addresses**:  
   ![Update the file with the revised list of IP addresses](Screenshots/Updating_with_Revised_IP.png)

## Prerequisites

- Python 3.x
- Basic knowledge of file handling in Python

## Result

- **allow_list.txt** will be updated, removing any IPs listed in **remove_list.txt**.

## Benefits

- **Automation**: Simplifies a tedious manual process, saving time and reducing errors.
- **Maintain Security**: Ensures unauthorized IPs are removed from the allow list, keeping sensitive content secure.
- **Scalable Solution**: Easily adapts to larger allow lists or more complex IP management needs.

## Future Improvements

- **Add Logging**: Monitor the removal process for better traceability.
- **Backup Mechanism**: Implement a backup mechanism for the original allow list before modifications.
- **Error Handling**: Include error handling for file access issues or invalid IP formats to enhance robustness.
