
# Chrome Credentials Extractor

## Overview

Chrome Credentials Extractor is a Python script designed to extract and decrypt saved login credentials from Google Chrome. This tool is intended for educational and ethical hacking purposes, helping users understand how data can be retrieved and decrypted from a system.

## Features

- Extracts the AES encryption key from Chrome's local state file.
- Copies Chrome's SQLite database to allow reading while Chrome is running.
- Decrypts saved login credentials (URLs, usernames, passwords).
- Saves the extracted credentials into a formatted Excel file.

## Requirements

- Python 3.x
- Libraries: 
  - `os`
  - `sys`
  - `shutil`
  - `sqlite3`
  - `base64`
  - `json`
  - `win32crypt`
  - `pycryptodome`
  - `pandas`
  - `openpyxl`

You can install the required libraries using pip:

```sh
pip install pycryptodome pandas openpyxl
```

## Usage

1. Clone the repository or download the script file.
2. Ensure you have the required Python libraries installed.
3. Run the script using Python:

```sh
python chrome_creds_extractor.py
```

4. The script will extract and decrypt the credentials, saving them into an Excel file named `chrome_creds.xlsx`.

## Script Details

### Function: `chrome_creds_extractor()`

1. **Extract AES Key**:
   - Reads the AES key from Chrome's local state file located at `%USERPROFILE%\AppData\Local\Google\Chrome\User Data\Local State`.
   - Decrypts the key using Windows Data Protection API (DPAPI).

2. **Copy SQLite Database**:
   - Copies the Chrome login data database from `%USERPROFILE%\AppData\Local\Google\Chrome\User Data\default\Login Data` to a temporary file `chrome_db_temp.db`.

3. **Read and Decrypt Login Data**:
   - Connects to the copied SQLite database and retrieves login information.
   - Decrypts the passwords using the extracted AES key.

4. **Print and Save Data**:
   - Prints the decrypted login information to the console.
   - Saves the data into a pandas DataFrame and writes it to an Excel file `chrome_creds.xlsx`.

5. **Format Excel File**:
   - Applies formatting to the Excel file, including column widths, colors, text wrapping, and freezing the top row.

6. **Clean Up**:
   - Deletes the temporary database file.

### Example Output

The script will generate an Excel file with the following columns:

- Origin URL
- Action URL
- Username
- Password

Each cell will be formatted for better readability.

## Legal and Ethical Considerations

This script is intended for educational purposes and ethical hacking practices only. Unauthorized access to data or systems is illegal and unethical. Always obtain explicit permission before testing or extracting data from any system.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Contributing

Contributions are welcome! Please fork the repository and submit a pull request with your changes.

## Contact

If you have any questions or need further assistance, please open an issue or contact the repository owner.
