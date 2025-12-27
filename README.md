# NSA (Network Security Auditor) 

**NSA** is a high-efficiency automation tool built for security professionals to identify critical misconfigurations. It simplifies complex scanning tasks into a single, interactive interface with real-time feedback and clean, summarized reporting.

---

## 🛠️ Installation & Prerequisites

Before running the tool, ensure your Kali Linux environment is updated and the necessary dependencies are installed.

### 1. Install Dependencies

Run the following command to install `nmap` (with NSE scripts), `snmp-check`, and `redis-tools`:


```sh
sudo apt update && sudo apt install nmap snmp-check redis-tools dos2unix -y
```

### 2. Clone the Repository


```sh
git clone https://github.com/Hari-prasaanth/NSA.git
cd NSA
```

### 3. Fix Line Endings (CRLF to LF)

If you encounter errors like `\r command not found`, use `dos2unix` to fix the script formatting:

```sh
dos2unix NSA.sh
```

### 4. Set Permissions

```sh
chmod +x NSA.sh
```

---

## 📖 Manual (Usage)

### Input File Format

The tool requires a `.txt` file containing your target list. The expected format per line is `IP Port Number`.

**Example `targets.txt`:**

```
  XX.XX.XX.XX Port XXX
  XX.XX.XX.XX Port XXX
```

### Execution

Launch the auditor by passing the target file as an argument:


```
./NSA.sh targets.txt
```

---

## 🚀 Key Modules

Once launched, the **NSA** menu allows you to select from the following modules:

- **NTP monlist (DoS):** Scans for NTP servers allowing the `monlist` command (CVE-2013-5211).
    
- **NTP Mode 6 Scanner:** Identifies information disclosure via NTP control queries.
    
- **SNMP Default Community (public):** A comprehensive check that flags the host if `public` access reveals System Info, Network Interfaces, Processes, or Storage data.
    
- **SMB Signing Not Required:** Finds hosts where SMB signing is disabled, indicating vulnerability to NTLM relay attacks.
    
- **AMQP Cleartext Authentication:** Checks for plaintext credential transmission on RabbitMQ/AMQP services.
    
- **Redis Vuln Checker:** Identifies Redis instances allowing unauthenticated remote access.
    

---

## 🖥️ User Interface Flow

The tool provides a clean, "GUI-like" terminal experience.

### Menu Display


```sh
========================================
      Network Security Auditor v1.2
========================================
1. NTP monlist (DoS)
2. NTP Mode 6 Scanner
3. SNMP Default Community (public)
4. SMB Signing Not Required
5. AMQP Cleartext Authentication
6. Redis Vuln Checker (Unauthenticated Access)

Select an option [1-6]: _
```

### Real-time Tracking

During the scan, the tool suppresses raw output and displays a localized progress bar to keep the workspace clean: `Progress: [3/16] Scanning XX.XX.XX.XX...`

---

## 📊 Standardized Report Output

After the scan completes, a summary is displayed with color-coded results:


```
----------------------------------------
Vulnerable IPs:
  XX.XX.XX.XX Port XXX
  XX.XX.XX.XX Port XXX

Not Vulnerable IPs:
  XX.XX.XX.XX Port XXX

Stats:
Total IPs inputted: 10
Total vulnerable IP: 2
Total non vulnerable IP: 8
----------------------------------------
```

---

## ⚠️ Disclaimer

_This tool is intended for legal, authorized security testing and educational purposes only. The developer assumes no liability for misuse or damage caused by this script._
