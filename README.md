# Chrome-Credentials-Extractor
This script extracts usernames and passwords from Google Chrome for each website that the user has locally stored their credentials. The extracted credentials are saved into an Excel file (chrome_creds.xlsx).

Features
Extracts and decrypts saved passwords from Google Chrome.
Saves the extracted credentials into a well-formatted, colorized Excel file.
Applies text wrapping and column width adjustments for better readability.
Highlights the header row and freezes it for easy navigation.
Requirements
Python 3.x
Required Python packages: pandas, openpyxl, pycryptodome, pywin32
Installation
Clone the repository:

bash
Copy code
git clone https://github.com/yourusername/chrome-credentials-extractor.git
cd chrome-credentials-extractor
Install the required packages:

bash
Copy code
pip install pandas openpyxl pycryptodome pywin32
Usage
Ensure Google Chrome is closed before running the script to allow access to the Login Data database.

Run the script:

bash
Copy code
python chrome_creds_extractor.py
The script will generate an Excel file (chrome_creds.xlsx) with the extracted credentials.

Script Overview
chrome_creds_extractor.py
This script performs the following steps:

Extract the AES key:

Reads the key from %USERPROFILE%\AppData\Local\Google\Chrome\User Data\Local State.
Decodes and decrypts the key using the win32crypt library.
Copy and query the Chrome database:

Copies the Login Data SQLite database to avoid access issues while Chrome is running.
Queries the database to retrieve URLs, usernames, and encrypted passwords.
Decrypt the passwords:

Decrypts the passwords using the extracted AES key and the pycryptodome library.
Save the credentials to an Excel file:

Saves the extracted credentials into an Excel file (chrome_creds.xlsx) using the pandas library.
Applies formatting, text wrapping, and column width adjustments for readability.
Colorizes each column and freezes the header row for easy navigation.
Security Considerations
Ensure the script is run in a secure environment as it deals with sensitive information.
Do not share or expose the generated chrome_creds.xlsx file as it contains decrypted passwords.
Contributing
Contributions are welcome! Please open an issue or submit a pull request if you have any improvements or suggestions.

License
This project is licensed under the MIT License. See the LICENSE file for details.
