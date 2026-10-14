<h4 align="right">
  <span style="margin:0 10px;color:#24292f">English</span>
  <a href="./README.md">简体中文</a>
</h4>
<p align="center">
<img src="https://jjp-c3e.pages.dev/1.png" width="300"/>
</p>
<h1 align="center">JJP · Self-developed Private Encryption Container Specification</h1>
<p align="center">
Built as static web page. All calculations run locally inside browser sandbox. No user files will be uploaded to remote servers.
</p>
<p align="center">
<a href="https://github.com/jjp117/jjp/releases">
<img src="https://img.shields.io/github/v/release/jjp117/jjp?style=flat-square&logo=github" alt="Release">
</a>
<a href="https://github.com/jjp117/jjp/stargazers">
<img src="https://img.shields.io/github/stars/jjp117/jjp?style=flat-square&logo=github" alt="Stars">
</a>
<a href="https://github.com/jjp117/jjp/blob/main/LICENSE">
<img src="https://img.shields.io/github/license/jjp117/jjp?style=flat-square&logo=github" alt="License">
</a>
</p>
<br>
<p align="center">
<a href="https://jjp-c3e.pages.dev/" target="_blank">
<img src="https://img.shields.io/badge/🔗Open-JJP_Web-2563eb?style=for-the-badge&logo=https://jjp-c3e.pages.dev/1.png&logoColor=white" width="320" alt="Open JJP Web">
</a>
&nbsp;&nbsp;
<a href="https://github.com/jjp117/jjp/releases" target="_blank">
<img src="https://img.shields.io/badge/📥Download-Releases-red?style=for-the-badge&logo=github&logoColor=white" width="320" alt="Download Releases">
</a>
</p>

# JJP
## What is JJP
JJP is a private container format. It packages arbitrary files into one single file, and encrypts content with AES-GCM symmetric encryption. Passwords are never stored inside JJP files. The decryption key is derived from your password via PBKDF2.

## Design Goal
JJP is designed for non-technical users: simple, zero-dependency file packaging and encryption. No software installation, no environment setup, no command line required. You only need a web browser to encrypt or decrypt files.

## Working Principle
All encryption and decryption operations run locally in your browser, powered by the Web Crypto API. There is no backend server, no data upload, and no extra network requests during processing.

## Encryption Specification
Algorithm: AES-256-GCM.
The encryption key is derived using PBKDF2-HMAC-SHA256 with 100,000 iterations.
A unique random salt and initialization vector (IV) will be generated for every encryption task.

## Integrity Verification
AES-GCM includes an authentication tag. If the file is tampered, corrupted, or an incorrect password is supplied, decryption will fail directly and will not output damaged data.

## Format Features
JJP is a custom private container format defined by the author. Full specification documents are stored in this repository. It is NOT an international public standard. Mainstream software cannot natively parse `.jjp` files. Only this project supports JJP container encryption and decryption.

## Usage
Open the web page to start. Drag files into the page and enter your password to generate a `.jjp` container. Drag the `.jjp` container into the page and input the same password to restore the original file. No installation, no registration, and internet access is not required.
> Web Address: https://jjp-c3e.pages.dev/

## ⚠️ Browser Compatibility Notice
Requires Web Crypto API. Old browsers (Safari 11 on macOS 10.13 High Sierra) have incomplete WebCrypto implementation and may fail while processing large files. Recommended browsers: Chrome / Firefox. You can also use desktop clients packaged by PakePlus v0.2.13.

## Security Statement
JJP provides standard symmetric encryption to prevent casual inspection of your files. It is NOT enterprise-grade or military-grade encryption. Do NOT use it for corporate secrets, government data, financial records or other high-value confidential information.

## Password Management
JJP never stores your password. There is no password recovery mechanism. If you lose your password, the JJP file cannot be decrypted. Please keep your password safe, and avoid sending the password and encrypted file through the same channel.

## Applicable Scenarios
Personal file packaging, small-scale file sharing, basic privacy protection for non-highly-sensitive content.

## Known Limitations
- Large files may trigger memory limits on older browsers
- AES-GCM has a maximum single-encryption data size limit
- The entire `.jjp` file must be fully loaded before decryption; streaming random access is not supported

## Open Source Information
The primary release form is a static web page. Desktop clients can be packaged with PakePlus. There is no native CLI version. The web frontend is open-source; press F12 in your browser to view the source code and implementation.

## License
This project is released under the MIT License.

This project is open-source under MIT License.
