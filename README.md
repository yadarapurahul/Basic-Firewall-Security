# Basic-Firewall-Security
Firewall configuration on Linux using UFW - blocking Telnet, allowing SSH, and managing network traffic rules.

## Tools Used
- **Kali Linux**
- **UFW (Uncomplicated Firewall)**

---

## Steps Performed

### 1. Install and Enable UFW 
- Open Kali linux in your machine then open terminal
- firstly you update the kali linux using **sudo apt update && sudo apt upgrade**
- Install the Uncomplicated Firewall using **sudo apt install ufw -y**
- Then Enable the Uncomplicated firewal using **sduo ufw enble**
- Checking the any firewall rule are signed or not uisng **sudo ufw status verbose**

### 2. List Current Firewall Rules
 - seeing the current Firewall rule list but in my linux didn't list any firewall rules by using **sudo ufw status numbered**

### 3. Block Inbound Traffic on Port 23 (Telnet)
- Firstly I was blocking the port 23 using sudo ufw deny 23/tcp.
- In Telnet sends username and password in plain text (not encrypted).
- Blocking port 23 helps prevent unauthorized acces via the Telnet protocol, which is known to be insecure. On modern systems, Telnet should be disabled and blocked unless absolutley necessary.
- you can check wheather it is block or not using **sudo ufw status numbered**

### 4. Test the Rule
- **telnet localhost 23**
- You will not be able to connect to port 23 on your local machine.
- Depending on your system and firewall behavior, you'll likely see one of these:
   - *connection refused* -> Means the firewall or OS is actively rejecting the connection.
   - *connection timed out* -> Means the firewall is silently dropping the connection packets.

### 5. Allow SSH (Port 22)
- Then I was allowing SSH port using **sudo ufw allow 22/tcp.
- check the rule numbers which help to does the SSH port is allow or not
#### Why you should allow SSH
- **Remote Administration**
  - SSH lets you securely log into your Linux machine from another system.
  - If you manage a server remotely, blocking SSH willl lock you out.
- **Encrypted Communication**
    - Unlike Telnet, SSH encrypts all traffic (incluing passwords), prventing eavesdropping.
- **Essential for Secure Management**
    - You can securley run commands, transfer file (via scp or sftp), and tunnel otheer protocols through SSH.
- **Default Port for secure Access**
  Port 22 is the standard SSH port - most systems expect it to be open for remote admin.

### 6. Remove the Block Rule
- Removing or deleting the Block or deny firewall rules using **sudo ufw delete 1**.

## How Firwall Filters Traffic
A firewall acts as a barrier between your system and the network, filtering incoming and outgoing traffic based on rules.
- Inbound rules: Control traffic enetering your system.
- Outbound rules: Control traffic leaving your system.
- UFw simplifies firewall management with easy allow and deny commands.
By blocking unnecassary ports (e.g., Telnet) nd allowing essential ones (e.g., SSH), we reduce attack surfaces and improves security.
