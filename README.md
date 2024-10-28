# Automated IP Allow List Updater

## Project Description
This project automates the process of updating an IP allow list by removing unauthorized IP addresses. It’s especially useful for organizations that need to maintain restricted content access. The algorithm reads from an allow list file and a remove list, iterates through both, and updates the allow list by removing IP addresses in the remove list.

## Features
- **Read and Parse Files**: Reads IP addresses from a file containing the allow list and converts them into a manageable format.
- **List Conversion**: Transforms IP data from string format into a list for easier manipulation.
- **Automated IP Removal**: Iterates through a remove list and removes unauthorized IPs from the allow list.
- **File Update and Rewrite**: After processing, updates the allow list file with the revised IP addresses.

## Project Structure
- **allow_list.txt** - Contains the IP addresses allowed access to restricted content.
- **remove_list.txt** - Contains IP addresses that should be removed from the allow list.
- **update_script.py** - Python script to automate the allow list update.

## How It Works
1. **Opening the Allow List**: The script opens `allow_list.txt` using the `with` statement in read mode, making it easy to read the content and manage resources.
2. **Reading File Contents**: Reads the contents of the allow list file and stores them in a string format.
3. **Converting String to List**: Transforms the string of IP addresses into a list, allowing each IP to be accessed individually.
4. **Iterating Through the Remove List**: Goes through each IP in `remove_list.txt`, checking if it exists in the allow list.
5. **Removing IP Addresses**: If an IP from the remove list is found in the allow list, it’s removed using the `.remove()` method.
6. **Updating the Allow List**: The modified allow list is converted back to a string format, with each IP on a new line, and saved back to `allow_list.txt`.

## Code Overview
```python
# update_script.py

# Step 1: Open the Allow List File
with open("allow_list.txt", "r") as file:
    ip_addresses = file.read().splitlines()
```
**Opening the  file that contains the allow list**:
   ![Opening the file](Screenshots/Opening_File_with_Allow_List.png)

# Step 2: Convert String into List
ip_list = ip_addresses.split()

# Step 3: Open and Iterate Through the Remove List
with open("remove_list.txt", "r") as file:
    remove_list = file.read().splitlines()

# Step 4: Remove IPs from Allow List
for ip in remove_list:
    if ip in ip_list:
        ip_list.remove(ip)

# Step 5: Update the Allow List File
with open("allow_list.txt", "w") as file:
    file.write("\n".join(ip_list))

