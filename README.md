# Basic-Firewall-Security
Firewall configuration on Linux using UFW—blocking Telnet, allowing SSH, and managing network traffic rules.

## Tools Used
- **Kali Linux**
- **UFW (Uncomplicated Firewall)**

---

## Steps Performed

### 1. Install and Enable UFW 
- Open Kali Linux on your machine, then open the terminal.
- Firstly, you update the kali linux using **sudo apt update && sudo apt upgrade**
- Install the Uncomplicated Firewall using **sudo apt install ufw -y**
- Then Enable the uncomplicated firewall using **sudo ufw enable.**
- Checking if any firewall rule are signed or not using **sudo ufw status verbose**

### 2. List Current Firewall Rules
 - seeing the current Firewall rule list but in my Linux, it didn't list any firewall rules by using **sudo ufw status numbered**

### 3. Block Inbound Traffic on Port 23 (Telnet)
- Firstly, I was blocking the port 23 using sudo ufw deny 23/tcp.
- In Telnet, it sends username and password in plain text (not encrypted).
- Blocking port 23 helps prevent unauthorized access via the Telnet protocol, which is known to be insecure. On modern systems, Telnet should be disabled and blocked unless absolutely necessary.
- you can check whether it is block or not using **sudo ufw status numbered**

### 4. Test the Rule
- **telnet localhost 23**
- You will not be able to connect to port 23 on your local machine.
- Depending on your system and firewall behavior, you'll likely see one of these:
   - *connection refused* -> Means the firewall or OS is actively rejecting the connection.
   - *connection timed out* -> Means the firewall is silently dropping the connection packets.

### 5. Allow SSH (Port 22)
- Then I was allowing SSH port using **sudo ufw allow 22/tcp**.
- check the rule numbers which help to determine if the SSH port is allow or not
#### Why you should allow SSH
- **Remote Administration**
  - SSH lets you securely log into your Linux machine from another system.
  - If you manage a server remotely, blocking SSH will lock you out.
- **Encrypted Communication**
    - Unlike Telnet, SSH encrypts all traffic (including passwords), preventing eavesdropping.
- **Essential for Secure Management**
    - You can securely run commands, transfer files (via SCP or SFTP), and tunnel other protocols through SSH.
- **Default Port for secure Access**  
    - Port 22 is the standard SSH port—most systems expect it to be open for remote admin.

### 6. Remove the Block Rule
- Removing or deleting the block or deny firewall rules using **sudo ufw delete 1**.

## How a Firewall Filters Traffic
A firewall acts as a barrier between your system and the network, filtering incoming and outgoing traffic based on rules.
- Inbound rules: Control traffic entering your system.
- Outbound rules: Control traffic leaving your system.
- UFW simplifies firewall management with easy allow and deny commands.  
By blocking unnecessary ports (e.g., Telnet) and allowing essential ones (e.g., SSH), we reduce attack surfaces and improve security.
