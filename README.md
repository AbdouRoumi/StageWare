# MalwareStaging
### Overview
**R0m4InShell** is a proof-of-concept (PoC) project showcasing a malware staging website. It demonstrates how to download and inject a malicious payload (shellcode) into a target process on a remote system. The tool connects to a web server to retrieve the staged shellcode, injects it into the target process, and executes it.

This project highlights the techniques used in malware delivery and execution, including process injection and remote thread creation. It is intended for research, education, and security testing purposes.

### Features
- **Shellcode Staging**: Retrieves the shellcode from a remote URL.
- **Process Injection**: Injects shellcode into a running process using `CreateRemoteThread`.
- **Remote Payload Execution**: Executes the downloaded shellcode within the context of the injected process.
- **Detailed Logging**: Logs each step of the process from URL connection, downloading shellcode, process enumeration, and injection.

### Usage
1. **Configure Web Server**: Host the shellcode on a web server.
2. **Run the Tool**: Execute the binary with the target process name as an argument:
   ```
   R0m4InShell.exe <Process Name>
   ```
   Example:
   ```
   R0m4InShell.exe notepad.exe
   ```
3. **Monitor** the console output for detailed logs, including the shellcode download, process handling, and remote thread creation.

### How It Works
1. The tool establishes a connection to a remote web server and downloads a staged shellcode.
2. It then enumerates running processes to find the specified target.
3. Once the process is found, the tool allocates memory in the target process and writes the shellcode into it.
4. Finally, the shellcode is executed by creating a remote thread in the target process.

### Example Shellcode
The provided shellcode is a demonstration payload, but the tool can be adapted to use custom shellcodes for various purposes.

### Prerequisites
- Windows operating system.
- Visual Studio or any compatible C/C++ compiler.
- A web server hosting the shellcode.

### Disclaimer
This project is for educational and research purposes only. It should only be used in controlled environments, and the author does not endorse or encourage any illegal activities.

---

### Example Output
```
Connection has been established.
URL has been opened.
Downloaded 600 bytes.
Checking process: notepad.exe
Great! We found the process: notepad.exe with PID: 1234
Allocated 600-bytes with PAGE_EXECUTE_READWRITE permissions inside 1234
Wrote 600-bytes to process memory
We got handle on the Thread 5678 ----------0x000000000000
Waiting for thread to finish...
Thread finished executing.
```

---
