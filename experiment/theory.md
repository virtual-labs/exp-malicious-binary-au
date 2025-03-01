### Theory

####  Binary File
A binary file is a type of computer file that contains machine-readable code, which a computer can execute. These files are often programs (like .exe files on Windows) that tell the computer what to do. However, some binaries can be malicious, such as viruses or malware, designed to harm systems or steal data.

####  Import Table
The Import Table is a section in a binary file (specifically in the Portable Executable or PE format used by Windows) that lists all the external functions and libraries the binary needs to run. It details the tools the program uses from the operating system or other files (called Dynamic Link Libraries or DLLs). For example:

<p>KERNEL32.dll: Provides basic system functions like file operations.</p> <p>USER32.dll: Handles user interface elements like windows and buttons.</p> <p>WinINet.dll: Manages internet-related tasks like HTTP requests.</p> 
<p>By examining the Import Table, we can see what a binary is capable of doing, which helps us figure out if it might be dangerous.</p>

#### Why Analyze the Import Table?
Malware often uses specific functions that legitimate programs don’t typically need. For instance:

<strong>Network-related functions</strong> (e.g., InternetOpen or HttpSendRequest from WinINet.dll) might mean the binary communicates with a remote server, possibly to send stolen data or receive commands.
<strong>System-modifying functions</strong> (e.g., WriteFile or CreateRemoteThread) could indicate the binary is trying to change files or inject code into other programs, a common malware trick.
<p>
Analyzing the Import Table is a form of static analysis, where we study the binary without running it, making it safer than executing potentially harmful code.</p>

#### What is String Extraction?
String extraction is the process of finding and pulling out readable text (called "strings") from a binary file. A binary file is mostly machine code—numbers and instructions a computer understands—but it often contains human-readable text like URLs (e.g., http://example.com), IP addresses (e.g., 192.168.1.1), file paths (e.g., C:\Windows), or commands. These strings can give clues about what the binary does, especially if it’s malicious. For example:
</p>
<p>
A string like http://malicious-site.com might show the binary connects to a harmful server.</p>

String extraction is part of static analysis, meaning we examine the binary without running it, making it a safe way to investigate potential malware.