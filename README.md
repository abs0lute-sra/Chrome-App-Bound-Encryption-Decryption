# Chrome App-Bound Encryption Decryption

## Overview

Chrome’s **App-Bound Encryption (ABE)** was introduced in Google Chrome in version 127 to strengthen the security of sensitive data by binding decryption capabilities to specific applications, preventing misuse by other processes on the system. 

This tool decrypts App-Bound encrypted keys stored in Chrome's Local State file, using Chrome’s internal COM-based **IElevator** service. The tool provides a way to retrieve and decrypt these keys, which Chrome protects via App-Bound Encryption (ABE) to prevent unauthorized access to secure data like cookies (and potentially passwords and payment information in the future).

## Prerequisites

- **Operating System**: Windows
- **Build Tools**: Microsoft Visual Studio C++ or compatible compiler (e.g., MSVC `cl` command)
- **Libraries**: Requires the following libraries: `ole32.lib`, `oleaut32.lib`, `shell32.lib`, `version.lib`, and `comsuppw.lib`.

## Usage

Build using your preferred C++ compiler:

```bash
cl /EHsc chrome_decrypt.cpp oleaut32.lib shell32.lib advapi32.lib shlwapi.lib
```

Place the compiled executable within the Chrome application directory (e.g., C:\Program Files\Google\Chrome\Application) due to path validation constraints inherent in Chrome’s ABE.
Run the executable from the command line:
```bash
PS C:\Program Files\Google\Chrome\Application> .\chrome_decrypt.exe

----------------------------------------------
|  Chrome App-Bound Encryption - Decryption  |
|  Alexander Hagenah (@xaitax)               |
----------------------------------------------

[+] Found Chrome Version: 130.0.6723.70
[*] Starting Chrome App-Bound Encryption Decryption process.
[+] COM library initialized.
[+] IElevator instance created successfully.
[+] Proxy blanket set successfully.
[+] Retrieving AppData path.
[+] Local State path: C:\Users\ah\AppData\Local\Google\Chrome\User Data\Local State
[+] Base64 encrypted key extracted.
[+] Finished decoding.
[+] Key header is valid.
[+] Encrypted key retrieved: 01000000d08c9ddf0115d1118c7a00c04fc297eb...
[+] BSTR allocated for encrypted key.
[+] Decryption successful.
[+] DECRYPTED KEY: a5e700d6cfb16beee5e9c198789f5cd2d2b5d2debe648fe578a7504a638dc186
```

Further Links:

- [Google Security Blog](https://security.googleblog.com/2024/07/improving-security-of-chrome-cookies-on.html)
- [Chrome app-bound encryption Service](https://drive.google.com/file/d/1xMXmA0UJifXoTHjHWtVir2rb94OsxXAI/view)
- [snovvcrash](https://x.com/snovvcrash)

## Disclaimer

> [!WARNING]  
> This tool is intended for cybersecurity research and educational purposes. Ensure compliance with all relevant legal and ethical guidelines when using this tool.