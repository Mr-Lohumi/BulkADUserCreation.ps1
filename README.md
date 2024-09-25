# BulkADUserCreation.ps1


# Bulk Active Directory User Creation Script

## SYNOPSIS

This PowerShell script automates the bulk creation of user accounts in Active Directory (AD) using data from a CSV file. The script reads user details such as first name, last name, username, password, and Organizational Unit (OU) from the CSV file and creates the corresponding user accounts in AD.

## DESCRIPTION

This script simplifies the process of creating multiple Active Directory user accounts in bulk. It reads a CSV file that contains user details and creates accounts for each entry. The script supports custom Organizational Units (OU) for each user and allows you to set user passwords securely.

## Features

- Bulk create AD users based on CSV input.
- Assign users to specific Organizational Units (OUs).
- Securely set passwords for each user.
- Option to set passwords to never expire.
- Simple, efficient, and reusable.

## Requirements

- PowerShell (version 5.0 or later)
- Active Directory module for PowerShell
- CSV file containing user details
- Proper permissions to create user accounts in Active Directory

## CSV File Format

The script requires a CSV file with the following columns:

```csv
FirstName,LastName,Username,Password,OU
John,Doe,jdoe,P@ssw0rd1,OU=Users,DC=domain,DC=com
Jane,Smith,jsmith,P@ssw0rd2,OU=Users,DC=domain,DC=com
```

- **FirstName**: The user's first name.
- **LastName**: The user's last name.
- **Username**: The user's username (SamAccountName).
- **Password**: The password for the user (in plain text; the script converts this to a secure string).
- **OU**: The distinguished name (DN) of the Organizational Unit where the user will be created.

## How to Use

1. **Prepare the CSV file**:
   - Ensure the CSV file has the correct headers (`FirstName`, `LastName`, `Username`, `Password`, `OU`).
   - Enter the details of each user to be created.

2. **Run the Script**:
   - Open PowerShell and run the script, specifying the path to your CSV file:
     ```powershell
     .\BulkADUserCreation.ps1 -csvFilePath "C:\Path\To\UsersToCreate.csv"
     ```

3. **Watch the Output**:
   - The script will attempt to create each user account listed in the CSV.
   - Successful creations will be displayed in green; any errors will be displayed in red.

## Example

Here’s an example of how to use the script:

```powershell
.\BulkADUserCreation.ps1 -csvFilePath "C:\UsersToCreate.csv"
```

This will create the users listed in the `UsersToCreate.csv` file.

## Customization

- **Adding more attributes**: You can customize the script to add more attributes (e.g., department, manager, phone number) by modifying the `New-ADUser` command within the script.
  
- **Modify OU for all users**: If all users should be created in the same Organizational Unit, you can hard-code the OU path in the script or remove the `OU` column from the CSV.

## Notes

- The password is handled securely by converting the plain text value to a secure string in the script.
- Make sure you have the necessary permissions to create user accounts in the specified OUs.

## License

This script is licensed under the [MIT License](LICENSE).

