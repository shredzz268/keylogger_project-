# Keylogger with Encrypted Data Exfiltration 

This project is a basic proof-of-concept keylogger built in Python. It captures keystrokes, encrypts the data using Fernet (symmetric encryption), stores the logs locally with timestamps, and simulates exfiltration to a local server.

## Features

- Keylogging using the `pynput` library
- Encryption using `cryptography.fernet`
- Local storage of encrypted logs
- Simulated exfiltration to a Flask-based HTTP server
- Kill switch to stop logging
- Optional startup persistence (not enabled by default)

## Folder Structure

keylogger_project/
├── decryptor.py
├── encryptor.py
├── exfil.py
├── keylogger.py
├── kill_switch.txt
├── logs/
│ ├── encrypted_logs/
│ └── received/
├── main.py
├── server.py
├── venv/ (excluded from zip)

## Setup Instructions

1. Create and activate virtual environment:

python -m venv venv
source venv/bin/activate

2. Install required packages:

pip install pynput cryptography flask requests

3. Generate an encryption key using:

```python
from cryptography.fernet import Fernet
print(Fernet.generate_key())
Copy the key and use it in encryptor.py.

Create folder structure:

mkdir -p logs/encrypted_logs
mkdir -p logs/received
touch kill_switch.txt
How to Run
Start the Flask server in one terminal:


python server.py
Run the keylogger in another terminal:

python main.py
Keystrokes will be logged, encrypted, and sent to the server.

Kill Switch
To stop the keylogger, open kill_switch.txt and add the word:

kill
The script will detect it and exit automatically.

Decryption
Use decryptor.py to decrypt and view the logs saved in logs/encrypted_logs/
