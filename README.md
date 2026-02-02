# Python-File-Integrity-Monitoring-Lab
## Objectives
This lab builds on a Python-based File Integrity Monitoring (FIM) script to explore how file changes and file deletion events can be detected and logged. After validating basic monitoring functionality, the script was iteratively enhanced to improve visibility into integrity changes and to treat file deletion as a security-relevant event. Troubleshooting and validation steps were documented to ensure reliable detection behavior.


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

## Initial Steps
The Python script was written to perform continuous file monitoring using cryptographic hashing. When the script starts, it calculates a SHA-256 hash of the monitored file and stores it as a baseline. At regular intervals, the script recalculates the file’s hash and compares it to the previous value. If a difference is detected, the script identifies this as a file modification event. Each detected change is logged with a timestamp and written to a log file stored in the logs directory, while also displaying status updates in the terminal.

Once the script was completed, it was executed from the project directory using Command Prompt. The script ran continuously, monitoring the specified file without requiring restarts. While the script was running, it repeatedly checked the integrity of the monitored file at fixed intervals until manually stopped by the user.

To validate the effectiveness of the File Integrity Monitor, the monitored text file was opened using Notepad while the script was running. After modifying and saving the file, the script immediately detected the change and displayed a notification in the terminal. At the same time, a new entry was written to the log file, including a timestamp indicating when the modification occurred. This confirmed that the monitoring and logging functionality was working as intended.

The results of the lab confirmed that the script successfully detected file modifications in real time and logged each event consistently. The monitoring process continued without interruption, and log entries persisted even after the scriptwas stopped, providing clear evidence of detected changes.

  <p align="center">
  <img src="images/Screenshot (2).png" width="1000">
  <br>
  <em>Figure 1: FIM Initial Steps: Detecting File Changes</em>
</p>



## Enhancement 1: Displaying Cryptographic Hash Values
The initial implementation detected file changes but did not provide visibility into why a change was detected. To improve transparency and reinforce the integrity verification process, the script was enhanced to display cryptographic hash values before and after a file modification occurred.

The monitoring logic was updated to print both the previous hash and the current hash whenever a file change was detected. This allowed direct observation of how even small file edits result in completely different hash values. The enhanced output confirmed that detection was based on content integrity rather than file size or timestamps. After implementing this change, the monitored file was edited while the script was running, and the terminal output successfully displayed the hash values alongside a change notification. Corresponding log entries continued to be written to the log file, confirming that the enhancement did not disrupt existing logging behavior.

  <p align="center">
  <img src="images/Screenshot (3).png" width="1000">
  <br>
  <em>Figure 2: Displaying Cryptographic Hash Values</em>
</p>

## Enhancement 2: File-Deletion Monitoring
The monitoring logic was updated to print both the previous hash and the current hash whenever a file change was detected. This allowed direct observation of how even small file edits result in completely different hash values. The enhanced output confirmed that detection was based on content integrity rather than file size or timestamps. After implementing this change, the monitored file was edited while the script was running, and the terminal output successfully displayed the hash values alongside a change notification. Corresponding log entries continued to be written to the log file, confirming that the enhancement did not disrupt existing logging behavior.

The hashing logic was removed for this portion of the lab to focus specifically on file existence monitoring. The script was updated to track whether the monitored file was present during the previous check and compare it against the current state. When a file transitioned from “present” to “missing,” the script generated an alert in the terminal and wrote a DELETED event to a dedicated deletion events log file. This approach ensured that deletion was logged once per event and did not repeatedly spam the logs.

The script was configured to monitor a file located in a separate directory using an absolute file path, demonstrating that the monitoring tool does not need to reside in the same folder as the target asset.

  <p align="center">
  <img src="images/Screenshot (4).png" width="1000">
  <br>
  <em>Figure 3: File-Deletion Monitoring </em>
</p>


### Troubleshooting
During initial testing, the deletion event did not trigger as expected. Troubleshooting revealed that the monitored file path and filename must match exactly, and that the file must exist at the time the script starts in order for deletion to be detected. To validate this, a different test file was selected, and the filename was verified character-for-character to ensure accuracy. The file was then deleted directly from the Command Prompt using the full absolute path, eliminating any ambiguity about which file was being removed.

After these adjustments, the script successfully detected the deletion event. The terminal displayed an alert confirming the file was missing, and a corresponding entry appeared in the deletion events log. This confirmed that the detection logic was functioning correctly and highlighted the importance of precise path handling and controlled testing in security monitoring.


## Results
The enhanced script successfully demonstrated:
- Real-time detection of file content changes with visible hash comparisons
- Reliable logging of file deletion events
- Accurate monitoring of files located outside the script’s directory
- Proper troubleshooting and validation of detection logic
- Logs provided timestamped evidence of both modification and deletion events, reinforcing the effectiveness of the monitoring approach.
