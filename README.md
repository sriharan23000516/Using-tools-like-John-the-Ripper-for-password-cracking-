# Using-tools-like-John-the-Ripper-for-password-cracking
## AIM:
To crack password hashes using John the Ripper in Kali Linux.
## REQUIREMENTS:
- **Operating System:** Kali Linux / Ubuntu / Windows (with JtR binaries)
- **Tools:**
    - John the Ripper (Community/Pro version)
    - Hash generating tools (e.g., openssl, unshadow)
- **Test Data:**
    - /etc/shadow file (Linux hashed passwords)
    - Custom password-protected file (ZIP, RAR, etc.)
## ARCHITECTURE DIAGRAM:
```mermaid
flowchart TD
    A[Password Protected File / Hash] --> B[John the Ripper]
    B --> C[Select Attack Mode: Dictionary or Brute Force]
    C --> D[Load Wordlist / Charset Rules]
    D --> E[Password Cracking Process]
    E --> F[Recovered Passwords]
```
## DESIGN STEPS:
### Step 1: Install John the Ripper
```bash
sudo apt update
sudo apt install john -y
```

### Step 2: Prepare Hash File
- Extract hashes (Linux example):
```
unshadow /etc/passwd /etc/shadow > myhashes.txt
```
- For a ZIP file:
```
zip2john secret.zip > ziphash.txt
```
### Step 3: Run John the Ripper
- Dictionary Attack:
```
john --wordlist=/usr/share/wordlists/rockyou.txt myhashes.txt
```
- Brute Force (Incremental Mode):
```
john --incremental myhashes.txt
```
### Step 4: Show Cracked Passwords
```
john --show myhashes.txt
```
## PROGRAM:
1. **Hash Extraction** – Obtain password hashes from system files or encrypted archives.
2. **Attack Mode Selection** – Choose between dictionary, brute force, or hybrid.
3. **Cracking Phase** – John the Ripper runs through candidate passwords.
4. **Password Recovery** – Successfully cracked passwords are displayed.

## OUTPUT:
![WhatsApp Image 2025-10-08 at 09 24 27_a00b2aa3](https://github.com/user-attachments/assets/92e74f28-1870-4fec-9628-f94c7e1cb5f0)
![WhatsApp Image 2025-10-08 at 09 24 54_67c7d642](https://github.com/user-attachments/assets/9f236560-329d-451b-b741-c91839fc854c)
![WhatsApp Image 2025-10-08 at 09 25 41_06183451](https://github.com/user-attachments/assets/58839b94-1c17-430e-8852-68a05e120945)
![WhatsApp Image 2025-10-08 at 09 26 27_3e230089](https://github.com/user-attachments/assets/8a153a41-6d45-4db6-9742-efa2cc6e0be7)
![WhatsApp Image 2025-10-08 at 09 43 33_8bcaa631](https://github.com/user-attachments/assets/700c0550-518a-46db-a0a8-5e4a577032f2)










## RESULT:
The password hashes were successfully cracked using John the Ripper.

