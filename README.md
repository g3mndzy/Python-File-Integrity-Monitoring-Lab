# Python-File-Integrity-Monitoring-Lab
## Objectives
Understand how File Integrity Monitoring works at a fundamental level
Monitor a file for changes using cryptographic hashing
Detect changes in real time without restarting the script
Log file modification events with timestamps
Gain hands-on experience with Python scripting and command-line execution
## Tools & Technologies
Programming Language: Python
Python Libraries: hashlib, os, time (standard library)
Operating System: Windows
Editor: VS Code
Execution Environment: Windows Command Prompt (CMD)
## Implementation Summary
The Python script performs the following actions:
- Generates a SHA-256 hash of the monitored file
- Stores the initial hash as a baseline
- Continuously recalculates the file’s hash at a fixed interval
- Compares the current hash against the previous hash
- Detects changes and logs events with timestamps
- Writes detection results to both the terminal and a log file
- The script runs continuously until manually stopped by the user

## Steps
The Python script was written to perform continuous file monitoring using cryptographic hashing. When the script starts, it calculates a SHA-256 hash of the monitored file and stores it as a baseline. At regular intervals, the script recalculates the file’s hash and compares it to the previous value. If a difference is detected, the script identifies this as a file modification event. Each detected change is logged with a timestamp and written to a log file stored in the logs directory, while also displaying status updates in the terminal.

Once the script was completed, it was executed from the project directory using Command Prompt. The script ran continuously, monitoring the specified file without requiring restarts. While the script was running, it repeatedly checked the integrity of the monitored file at fixed intervals until manually stopped by the user.

To validate the effectiveness of the File Integrity Monitor, the monitored text file was opened using Notepad while the script was running. After modifying and saving the file, the script immediately detected the change and displayed a notification in the terminal. At the same time, a new entry was written to the log file, including a timestamp indicating when the modification occurred. This confirmed that the monitoring and logging functionality was working as intended.

The results of the lab confirmed that the script successfully detected file modifications in real time and logged each event consistently. The monitoring process continued without interruption, and log entries persisted even after the script was stopped, providing clear evidence of detected changes.

## Creating Hash Values
After validating the initial implementation, the script was enhanced to display cryptographic hash values during change detection. The monitoring target was then updated to a newly created file, allowing verification that the detection logic functioned consistently across different assets. When the monitored file was modified, the script successfully identified the hash change, displayed both previous and current hash values in the terminal, and logged the event with a timestamp. This confirmed the reliability and flexibility of the file-level integrity monitoring process.
