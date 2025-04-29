# Military-Grade SFTP Downloader

A bulletproof SFTP file downloader with automatic resume, connection stability features, and transfer optimization.

## Features
-  Chunked transfer protocol (2MB chunks)
-  Automatic resume from breakpoint
-  Connection keepalives and TCP optimizations
-  Progressive retry logic (7 attempts, 5s-10m delays)
-  Cross-platform support (Linux, macOS, Windows)
-  File tracking to only download new files
-  Server directory synchronization
-  Comprehensive logging

## Requirements
- Python 3.6+
- Paramiko ('pip install paramiko')
- python-dotenv ('pip install python-dotenv')

## Installation
1. Clone this repository
2. Install dependencies:
    '''bash
   pip install paramiko python-dotenv
3. Create a .env file with your configuration (see .env.example below)
	Configuration
	Create a .env file with these variables:
		SFTP_HOST=your.sftp.server.com
		SFTP_PORT=22
		SFTP_USER=username
		SFTP_PASS=password
		SFTP_DIR=/remote/path
		LOCAL_DIR=./downloads
		SERVER_DIR=./server
		LOG_FILE=./sftp_downloader.log
		LAST_FILE_RECORD=./last_file.txt

	Usage
		Run the script:
			python FTP_IPI.py
		
		The script will:
			1. Connect to the SFTP server
			2. Check for new files (containing 'IPI' in filename)
			3. Download the earliest new file not already downloaded
			4. Sync the file to the server directory
			5. Record the downloaded filename for next run

	Logging
		Logs are written to both console and the specified log file with timestamps.
		Example log output:
			[2023-05-15 14:30:45] INFO: Attempt 1 of 7
			[2023-05-15 14:30:46] INFO: Target file size: 45.67MB
			[2023-05-15 14:30:46] INFO: Resume point: 0 bytes (0.00MB)
			[2023-05-15 14:31:15] INFO: Progress: 25.3% | Speed: 512.4KB/s | Position: 11.56MB

	Error Handling
		The script will automatically retry failed operations with increasing delays. After 7 failed attempts, it will exit with an error message.

	License
		MIT License


This documentation provides a comprehensive overview of the script's functionality, setup instructions, and usage guidelines. The README.md can be used directly in your project repository.