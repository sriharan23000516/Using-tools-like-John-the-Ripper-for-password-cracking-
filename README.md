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
![WhatsApp Image 2025-10-08 at 09 24 27_063a01eb](https://github.com/user-attachments/assets/b5046aea-596d-47e1-85c5-668e71cad292)
![WhatsApp Image 2025-10-08 at 09 24 54_7d39aafa](https://github.com/user-attachments/assets/98ac2e9d-82b2-472f-93a7-df31a3d2f692)
![WhatsApp Image 2025-10-08 at 09 25 41_299b5d73](https://github.com/user-attachments/assets/903d6813-7932-41c9-9b90-1ba0cf003dc0)
![WhatsApp Image 2025-10-08 at 09 26 27_21e84107](https://github.com/user-attachments/assets/e53cf19e-b3fe-48af-b15f-f9392819f6b1)
![WhatsApp Image 2025-10-08 at 09 43 33_9c4d563a](https://github.com/user-attachments/assets/f49cd93b-1940-4697-9b2b-b49527516894)








## RESULT:
The password hashes were successfully cracked using John the Ripper.

