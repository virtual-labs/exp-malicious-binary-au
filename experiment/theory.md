### Theory
Malware analysis is a critical aspect of cybersecurity, enabling analysts to understand how malicious software operates and devising strategies to mitigate its impact. In this experiment, we focus on two primary aspects of malware analysis: the examination of a binary's Import Table and the extraction of strings from the binary to identify network connections.

##### Import Table Analysis:

The Import Table is a crucial component of a Portable Executable (PE) file, which includes the list of external functions and libraries that the binary requires to run. By analyzing this table, analysts can infer the capabilities of the binary and detect potentially malicious activities. For instance, if a binary imports HTTP-related Win32 APIs such as WinHttpOpen or InternetOpen, it suggests that the binary may establish network connections, potentially to malicious domains.

Understanding the Import Table involves recognizing the significance of the listed functions and libraries. For example, APIs related to network communication, file handling, or system manipulation are red flags that the binary might be engaging in suspicious activities. By methodically examining these imports, an analyst can form a hypothesis about the binary's behavior, which is crucial for the next steps in the analysis process.

##### String Extraction and Analysis:

Strings embedded within a binary can reveal significant insights into its functionality. These strings may include URLs, file paths, or commands that the binary uses during execution. The strings command is a common tool used to extract these readable ASCII strings from a binary file. By filtering these strings using specific patterns, such as "http://" or "https://", analysts can quickly identify the domains or IP addresses the binary is attempting to contact.

This process is particularly useful in network-based malware, where the binary connects to command-and-control (C2) servers. By identifying these connections, analysts can block the domains or IP addresses at the network level, preventing the malware from communicating with its operators and mitigating its impact.