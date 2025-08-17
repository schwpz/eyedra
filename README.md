# 👁️ Eyedra

![alt text](https://github.com/schwpz/eyedra/blob/main/eyedra%20logo.png)

Eyedra is a secure Windows utility for splitting and merging files with robust encryption, mandatory Two-Factor Authentication (2FA), user-specific wallet codes (public keys), and a private key system.  
**Eyedra is specifically designed for confidential file sharing:** every user's files are cryptographically protected so that only the intended recipient, with their private key, can decrypt files sent to their wallet code—providing true zero-knowledge security and safe file sharing.

---

## 🔑 Potential Use Cases

1. **Journalists & Media Organizations**  
   *Why?* Need to protect sources and share sensitive documents securely.  
   *Example:* Secure document exchange between reporters, activists, and newsrooms.  
   *Advantage:* With private key + 2FA, no outsider can decrypt shared files.

2. **Human Rights & Activist NGOs**  
   *Why?* Sensitive data and documents are frequently exchanged digitally.  
   *Example:* Confidential sharing among NGOs, vulnerable groups, or international activists.  
   *Advantage:* Zero-knowledge ensures source anonymity and confidentiality.

3. **Legal & Attorney Offices**  
   *Why?* Client files are extremely privacy-sensitive.  
   *Example:* Secure transfer of case files, contracts, and evidence between parties.  
   *Advantage:* Only users with the correct private key can decrypt files.

4. **Finance & Crypto Sector**  
   *Why?* Wallet code logic and key security is familiar and essential to crypto users.  
   *Example:* Confidential sharing of financial reports, investment docs, token/contract files.  
   *Advantage:* Crypto users are already comfortable with private/public key concepts.

5. **Academia & Research Communities**  
   *Why?* Preventing leaks and premature disclosure of research is critical.  
   *Example:* Sharing paper drafts, patent applications, or datasets securely.  
   *Advantage:* Only the intended recipient can decrypt, minimizing leak risk.


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


## 🛣️ Roadmap

### 1️⃣ Short-Term Goals (Next Release)
- Implement a **file sharing plugin** for one-time file downloads.  
- Make the GUI more **user-friendly**.  
- Minor **bug fixes** and performance improvements.

---

## 📦 Download

Always get the latest version from the [Releases](../../releases) section.

---

## 🔑 How it works?


![Eyedra User Flow](./Eyedra%20user%20flow%20.png)

---

## 📝 License & Usage

MIT License

Copyright (c) 2025 Batuhan Turguteli

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

---

## 🆘 Support & Feedback

Open an issue in the [Issues](../../issues) tab for help or to report bugs.  
Your feedback improves Eyedra!
