# JJP

这是什么：JJP 是一种私有容器格式，用于把任意文件封装成一个统一格式的单文件，并对文件内容执行 AES-GCM 对称加密。密码不会以任何形式存储在生成的文件中，解密所需的密钥由用户密码通过 PBKDF2 派生得到。
What is this: JJP is a proprietary container format designed to encapsulate arbitrary files into a single unified file, and to apply AES-GCM symmetric encryption to the file content. The password is never stored in the generated file in any form. The decryption key is derived from the user's password via PBKDF2.

设计目标：JJP 的设计目标，是为非专业用户提供一种简单、直接、零依赖的文件封装与加密方式。使用者无需安装任何软件、无需配置运行环境、无需掌握命令行，只需通过浏览器即可完成加密与解密。
Design goal: The design goal of JJP is to provide a simple, direct, and zero-dependency file encapsulation and encryption method for non-professional users. Users do not need to install any software, configure any runtime environment, or master the command line. Encryption and decryption can be completed entirely within a browser.

运行方式：JJP 完全运行在浏览器本地。所有加密与解密操作，均通过浏览器内置的 Web Crypto API 完成，不依赖任何后端服务，不上传任何数据，不产生任何网络请求。
How it runs: JJP runs entirely locally in the browser. All encryption and decryption operations are performed through the browser's built-in Web Crypto API. It does not rely on any backend service, does not upload any data, and does not generate any network requests.

加密方式：JJP 使用 AES-GCM 作为加密算法，密钥长度为 256 位。密钥由用户密码通过 PBKDF2 派生，迭代次数为 100,000 次，哈希算法为 SHA-256。每次加密都会生成新的随机盐值与初始化向量。
Encryption: JJP uses AES-GCM as the encryption algorithm, with a key length of 256 bits. The key is derived from the user's password via PBKDF2, with 100,000 iterations and SHA-256 as the hash algorithm. A new random salt and initialization vector are generated for every encryption.

完整性校验：AES-GCM 自带认证标签，可在解密时校验数据是否被篡改。若文件被修改、损坏，或密码错误，解密过程将直接失败并返回错误提示，不会输出任何错误内容。
Integrity verification: AES-GCM includes an authentication tag, which can verify whether the data has been tampered with during decryption. If the file has been modified, corrupted, or the password is incorrect, the decryption process will fail immediately and return an error message, without outputting any incorrect content.

格式特性：JJP 是一种私有格式。文件结构由本项目的作者自行定义，未公开完整规范。由于该格式未被任何公开标准收录，也不被任何现有软件兼容，因此外部工具无法直接识别、解析或打开 JJP 文件。
Format characteristics: JJP is a proprietary format. The file structure is defined by the author of this project, and the complete specification is not publicly disclosed. Since the format is not included in any public standard and is not compatible with any existing software, external tools cannot directly identify, parse, or open JJP files.

使用方式：打开网页版即可使用。用户将文件拖入页面，输入密码，即可生成 JJP 文件；将 JJP 文件拖入页面，输入相同密码，即可还原原始文件。整个过程无需安装、无需注册、无需联网。
Usage: Open the web version and use it directly. Users drag a file into the page and enter a password to generate a JJP file. To restore the original file, drag the JJP file into the page and enter the same password. The entire process requires no installation, no registration, and no internet connection.

网页版：https://123-a2r.pages.dev/
Web version: https://123-a2r.pages.dev/

安全性说明：JJP 提供的是常规强度的对称加密，能够有效防止文件被随意查看。但 JJP 并非商业级或军事级加密方案，不适合用于保护企业机密、政府数据、金融信息或其他高价值敏感内容。
Security note: JJP provides symmetric encryption of conventional strength, which can effectively prevent files from being casually viewed. However, JJP is not a commercial-grade or military-grade encryption solution. It is not suitable for protecting corporate secrets, government data, financial information, or other high-value sensitive content.

密码管理：JJP 不存储密码，也不提供密码找回功能。密码一旦遗失，文件将无法解密。建议使用者妥善保存密码，并避免将密码与加密文件通过同一条通道发送。
Password management: JJP does not store passwords and does not provide password recovery. Once the password is lost, the file cannot be decrypted. Users are advised to keep their passwords safe and avoid sending the password and the encrypted file through the same channel.

适用场景：JJP 适用于个人文件封装、小范围文件分享、非正式场合下的内容保护，以及任何不涉及高价值敏感信息的加密需求。
Use cases: JJP is suitable for personal file encapsulation, small-scale file sharing, content protection in informal settings, and any encryption needs that do not involve high-value sensitive information.

开源说明：JJP 的网页端为公开访问，任何人都可以在浏览器中按 F12 查看页面源代码，了解其实现方式。项目不提供独立的分发文件，也不提供命令行版本，所有功能均以网页形式交付。
Open source note: The web version of JJP is publicly accessible. Anyone can press F12 in the browser to view the page source code and understand its implementation. The project does not provide standalone distribution files or a command-line version. All functionality is delivered in the form of a web page.

许可：本项目以 MIT 许可证开源。
License: This project is open-sourced under the MIT License.
