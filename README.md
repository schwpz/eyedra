# 👁️ Eyedra

![alt text](https://github.com/schwpz/eyedra/blob/main/eyedra%20logo.png))

Eyedra is a secure Windows utility for splitting and merging files with robust encryption, mandatory Two-Factor Authentication (2FA), user-specific wallet codes (public keys), and a private key system.  
**Eyedra is specifically designed for confidential file sharing:** every user's files are cryptographically protected so that only the intended recipient, with their private key, can decrypt files sent to their wallet code—providing true zero-knowledge security and safe file sharing.

---

## 🚀 How Eyedra Works – User Journey

### 1. Download & Launch
- Download the latest `Eyedra.exe` from the [Releases](../../releases) section.
- Double-click to launch. No install, no dependencies required.

### 2. Create Your Account (**2FA Required**)
- Register with a username and a strong password.
- **2FA is mandatory:**  
  - Scan the QR code using a TOTP app (Google Authenticator, Authy, etc.).
  - Enter your first 2FA code to finish setup.

### 3. Receive Your Unique Wallet Code (Public Key) & Private Key
- Upon account creation, Eyedra generates a **unique wallet code** for you.
- Your wallet code acts as your **public key**:  
  - Share your wallet code with others so they can send you files securely.
  - Your wallet code is safe to share; it cannot be used to decrypt your files.
- Your **private key** is deterministically derived from your credentials and wallet code using a secure key derivation function (KDF).
- **The private key is never stored on disk and only exists in memory during your session.**
- _All encryption/decryption for your files is performed with this private key._
- **If you lose your credentials or wallet code, you lose access to your private key and your files become permanently inaccessible.**

### 4. Login (**2FA Required**)
- Enter your username, password, and 2FA code.
- For any file action (split/merge), your private key is derived in memory after successful authentication.

---

## 🔐 Secure Confidential File Sharing – The Eyedra Way

- **To send a file to someone securely:**  
  - Obtain the recipient's wallet code (**public key**).
  - Split & encrypt the file using Eyedra, entering the recipient’s wallet code.
  - The resulting `.eyedra` files are encrypted so that **only the recipient’s private key** (in their authenticated session) can decrypt and merge them.
  - **Even if someone else obtains the recipient’s wallet code, they cannot decrypt files—only the private key holder can.**
- **To receive and decrypt a file:**  
  - Use your own account and credentials.
  - Your private key is derived in memory after authentication.
  - Eyedra uses your private key to decrypt any files that were encrypted to your wallet code.

---

## 🔐 Wallet Code & Private Key – Security Logic

- **Wallet Code (Public Key):**  
  - A user-specific public identifier, generated at registration.
  - Used by others to encrypt files for you; safe to share.
  - **Cannot be used to decrypt files, even if exposed.**
- **Private Key:**  
  - Derived from your credentials and wallet code using a secure algorithm (e.g., Argon2 or scrypt).
  - Used to decrypt files sent to your wallet code.
  - **Never stored on disk; only exists in RAM during your active session.**
- **File Security:**  
  - When you split a file for someone, each `.eyedra` chunk is encrypted using the recipient’s wallet code (public key), so that **only their private key can decrypt it**.
  - **It is impossible to decrypt files with just the wallet code or with any other private key.**
- **Sharing:**  
  - Only the private key owner of a wallet code can decrypt files sent to them.
  - Files are mathematically bound to the intended recipient’s private key; brute force or alternate keys cannot open them.

---

## 🛡️ Security Features

- **Mandatory 2FA (TOTP):**  
  Every session and file operation requires a fresh 2FA code.
- **Public/Private Key Encryption:**  
  Files can only be decrypted by the intended recipient’s private key, never with just the wallet code.
- **AES-256-GCM Encryption:**  
  Each chunk is encrypted using the derived private key.
- **Zero-Knowledge Local Storage:**  
  Eyedra never sends or stores your data externally. All user data, keys, wallet codes, and private keys are only ever available locally and, for private keys, only in-memory.
- **No Recovery Backdoor:**  
  If you lose your credentials or wallet code, you lose your private key. _Not even the developer can recover your files._
- **Multi-User Support:**  
  Each user has a unique wallet code and private key; all data is isolated per user.

---


## 🔒 What You Need To Remember

- **Your wallet code = your public key = your address for receiving encrypted files.**
- **Your private key = your access. Only you can decrypt files sent to your wallet code.**
- **Never share your credentials or private key.** Share your wallet code (public key) for secure receiving.
- **Files encrypted to a wallet code cannot be decrypted by anyone except the private key holder—even if the wallet code is leaked.**
- **If you lose your credentials or wallet code, your files are lost forever.**

---

## 📦 Download

Always get the latest version from the [Releases](../../releases) section.

---

## 📝 License & Usage

- Eyedra is for personal and non-commercial use only.
- Redistribution, modification, or rebranding is not allowed.
- All rights reserved © 2025 schwpz

---

## 🆘 Support & Feedback

Open an issue in the [Issues](../../issues) tab for help or to report bugs.  
Your feedback improves Eyedra!
