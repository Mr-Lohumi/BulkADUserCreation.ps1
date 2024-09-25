

# Bulk Active Directory User Creation Script

## Overview

This PowerShell script helps you create multiple Active Directory users at once using a CSV file. Just list your users in the CSV, and the script will take care of the rest.

## Requirements

- PowerShell (version 5.0 or later)
- Active Directory module
- CSV file with user details
- AD permissions to create users

## CSV Format

Your CSV file should look like this:

```csv
FirstName,LastName,Username,Password,OU
John,Doe,jdoe,P@ssw0rd1,OU=Users,DC=domain,DC=com
Jane,Smith,jsmith,P@ssw0rd2,OU=Users,DC=domain,DC=com
```

- **FirstName**: User’s first name
- **LastName**: User’s last name
- **Username**: User’s AD username
- **Password**: Plain text password (will be securely converted)
- **OU**: The Organizational Unit (in DN format)

## How to Run

1. Prepare your CSV with user details.
2. Run the script in PowerShell:

   ```powershell
   .\BulkADUserCreation.ps1 -csvFilePath "C:\Path\To\UsersToCreate.csv"
   ```

3. The script will create the users in AD, showing successes in green and any errors in red.

