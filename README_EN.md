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

## How it works
All encryption and decryption run locally in your browser, powered by Web Crypto API. No backend server, no data upload, no network requests during processing.

## Encryption Details
Algorithm: AES-256-GCM. Key derived by PBKDF2-HMAC-SHA256, 100,000 iterations. A unique random salt and IV will be generated every encryption.

## Integrity Verification
AES-GCM comes with authentication tag. If file is tampered, corrupted, or wrong password provided, decryption fails directly without leaking broken data.

## Format Features
JJP is a custom private container format defined by the author. Full specification documents are included in this repository. It is NOT a public standard. Mainstream software cannot natively parse `.jjp` files. Only this project can encrypt/decrypt JJP containers.

## Usage
Open the web page. Drag files into the page, input password to create `.jjp` container. Drag `.jjp` file in and enter the same password to restore original file. No install, no register, no internet required.
> Web Page: https://jjp-c3e.pages.dev/

## ⚠️ Browser Compatibility Notice
Requires Web Crypto API. Old browsers (Safari 11 on macOS 10.13 High Sierra) have incomplete WebCrypto implementation and may fail on large files. Recommended: Chrome / Firefox. You may also use desktop client packaged by PakePlus v0.2.13.

## Security Statement
JJP provides standard symmetric encryption to prevent casual inspection of your files. It is NOT enterprise-grade or military-grade encryption. Do NOT use it for corporate secrets, government, financial or high-value confidential data.

## Password
JJP never saves your password. There is no password recovery method. If you lose your password, your JJP file cannot be decrypted. Keep your password safe, and avoid sending password and encrypted file together.

## Suitable Use Cases
Personal file packaging, small-scale file sharing, basic privacy protection for non-highly-sensitive content.

## Known Limitations
- Large files may hit memory limits on old browsers
- AES-GCM has maximum data size limit in single encryption
- The whole `.jjp` file needs to be fully loaded for decryption; random streaming read is unsupported

## About Open Source
The main delivery is static web page. Desktop builds can be packed with PakePlus. No native CLI version. Web source code is open; press F12 in browser to view implementation.

## License
This project is open-source under MIT License.
