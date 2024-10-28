# Automated IP Allow List Updater

## Project Description
As part of my job, I regularly update files that determine which employees can access restricted content based on their IP addresses. This project automates the process by updating an IP allow list, removing specific IP addresses from an external remove list, and rewriting the allow list with only approved IPs.

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
    for element in remove_list:
        
 # Step 5: Remove IP addresses in remove list from allow list
        if element in ip_addresses:
            ip_addresses.remove(element)

# Step 6: Update the file with the revised IP addresses
ip_addresses = "\n".join(ip_addresses)
with open(import_file, "w") as file:
    file.write(ip_addresses)
