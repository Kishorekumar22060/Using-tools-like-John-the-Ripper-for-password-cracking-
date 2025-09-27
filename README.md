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
Cracked Passwords from Hash File
<img width="900" height="385" alt="image" src="https://github.com/user-attachments/assets/b9bac1ba-afb6-4e5d-b288-e6f8afa68c5b" />
<img width="1279" height="595" alt="image" src="https://github.com/user-attachments/assets/c3f31274-d2b8-4839-86d5-b2b57d69387b" />
<img width="1167" height="546" alt="image" src="https://github.com/user-attachments/assets/e96d94b2-a1e3-48e2-8ab9-4bb90bfc8cf9" />
<img width="1242" height="641" alt="image" src="https://github.com/user-attachments/assets/9488f2a8-dc38-4080-9e05-b920948c1cc9" />
<img width="866" height="385" alt="image" src="https://github.com/user-attachments/assets/b26c571f-4a70-4ed0-969d-34e693f57cdd" />

## RESULT:
The password hashes were successfully cracked using John the Ripper.

