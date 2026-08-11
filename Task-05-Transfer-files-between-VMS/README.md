# Task 05: File Transfer Between Virtual Machines

## Objective
To demonstrate file transfer between two virtual machines using SCP 
(Secure Copy Protocol) over SSH. Files are transferred in both 
directions to verify successful communication between VMs.

## Tools Used
- VMware Workstation
- Kali Linux VM (Original) - VM1
- Kali Linux VM (Clone) - VM2
- OpenSSH Server
- SCP Command

## Setup: Cloning the VM

### Step 1: Cloned Original Kali VM
Used VMware's Clone feature to create a duplicate VM (Kali-Linux-2) 
for testing file transfers between two virtual machines.

Steps:
- Right-click VM > Manage > Clone
- Selected "Create a linked clone" for faster cloning
- Named the clone as Kali-Linux-2

<img width="472" height="434" alt="Screenshot 2026-08-11 125030" src="https://github.com/user-attachments/assets/9c1ebdeb-3507-4036-ab8c-3ba33124f871" />


### Step 2: Both VMs Started
Started both VMs simultaneously in VMware Workstation:
- VM1: Kali Linux (Original)
- VM2: Kali Linux (Clone)


## Network Configuration

### Step 3: Network Adapter Configuration
Both VMs configured with NAT network adapter so they can communicate 
with each other on the same virtual network.

<img width="950" height="488" alt="Screenshot 2026-08-11 125425" src="https://github.com/user-attachments/assets/d772bbcb-1893-486c-96f6-e89ced616266" />


### Step 4: IP Addresses Identified
Ran the following command on both VMs to get their IP addresses:

    hostname -I

Or:

    ip addr show

Results:
- VM1 IP: 192.168.x.x
- VM2 IP: 192.168.x.x

<img width="1280" height="800" alt="Kali linux-2026-08-11-12-58-33" src="https://github.com/user-attachments/assets/3d333416-12e5-46f0-9709-2a333073e907" />

<img width="778" height="416" alt="image" src="https://github.com/user-attachments/assets/c0ae2ea4-056c-4957-a6cf-2a9fcb9deb36" />


### Step 5: Connectivity Tested
Tested connectivity between VMs using ping:

    ping 192.168.31.136

Successful ping responses confirmed both VMs could communicate.

<img width="807" height="434" alt="image" src="https://github.com/user-attachments/assets/b2a8f092-961c-4134-8efe-8615beec050f" />


## SSH Setup

### Step 6: OpenSSH Server Installed
Installed SSH server on both VMs to enable secure file transfer:

    sudo apt update
    sudo apt install openssh-server -y

<img width="1280" height="800" alt="Kali linux-2026-08-11-13-12-46" src="https://github.com/user-attachments/assets/657ae157-ae67-4196-9a3b-37fc38966b71" />


### Step 7: SSH Service Started and Enabled
Started SSH service and enabled it to run on boot:

    sudo systemctl start ssh
    sudo systemctl enable ssh
    sudo systemctl status ssh

SSH service showed "active (running)" status confirming it was working.

<img width="770" height="425" alt="image" src="https://github.com/user-attachments/assets/3e358c93-45d0-492f-a823-b49da1973c1f" />


## File Transfer

### Step 8: Test File Created on VM1
Created a test file on VM1's Desktop with sample content:

    cd ~/Desktop
    echo "Hello from VM1 - This is a file for transfer test" > test-file.txt
    echo "Task 05: File Transfer Between VMs" >> test-file.txt
    echo "Virtual Systems and Services Lab" >> test-file.txt
    echo "Created by Hifza" >> test-file.txt

Verified file content:

    cat test-file.txt

Output:
- Hello from VM1 - This is a file for transfer test
- Task 05: File Transfer Between VMs
- Virtual Systems and Services Lab
- Created by Hifza

<img width="1280" height="800" alt="Kali linux-2026-08-11-13-23-43" src="https://github.com/user-attachments/assets/ba28043b-1995-4376-9bb2-7828495a0524" />


### Step 9: File Transferred from VM1 to VM2 (SCP)
Used SCP command to transfer the file from VM1 to VM2:

    scp test-file.txt hifza@192.168.31.136:/home/hifza/Desktop/

The system asked for:
1. Host authenticity confirmation (typed: yes)
2. Password of VM2 user

File successfully transferred with 100% completion.

<img width="1280" height="800" alt="Kali linux-2026-08-11-13-31-41" src="https://github.com/user-attachments/assets/c882568d-f900-4422-ad05-8b149551e426" />


### Step 10: File Verified on VM2
Switched to VM2 and verified file was received:

    cd ~/Desktop
    ls
    cat test-file.txt

File was present with all content intact.

<img width="782" height="418" alt="image" src="https://github.com/user-attachments/assets/27e483be-5034-481e-9a7b-07fc85750133" />


### Step 11: Reply File Created on VM2
Created a reply file on VM2 to transfer back to VM1:

    cd ~/Desktop
    echo "Hello from VM2 - Reply from clone!" > reply.txt
    echo "File received successfully" >> reply.txt

[Screenshot: 12-create-file-vm2.png]

### Step 12: File Transferred from VM2 to VM1 (Reverse SCP)
Transferred file from VM2 back to VM1:

    scp reply.txt hifza@[VM1-IP]:/home/hifza/Desktop/

Password of VM1 entered when prompted. Transfer completed successfully.

<img width="1280" height="800" alt="Kali linux-2026-08-11-13-57-38" src="https://github.com/user-attachments/assets/a05a1dbc-bb1c-4e48-a49f-34fbbfdbcecb" />


### Step 13: File Verified on VM1
Verified the reply file was received on VM1:

    cd ~/Desktop
    ls
    cat reply.txt

Reply file received successfully with all content.

<img width="772" height="396" alt="image" src="https://github.com/user-attachments/assets/f3b5d9c5-d154-4b00-ad39-4edce0890ca9" />


## Conclusion
Successfully demonstrated file transfer between two virtual machines 
using SCP protocol over SSH. Files were transferred bidirectionally:
- From VM1 to VM2
- From VM2 to VM1

This demonstrates how virtual machines can communicate and share data 
in a cloud environment, which is essential for cloud computing operations 
like VM migration, data backup, and distributed computing.

## Commands Reference

| Command | Purpose |
|---------|---------|
| `hostname -I` | Display machine IP address |
| `ip addr show` | Show detailed network info |
| `ping [IP]` | Test connectivity between VMs |
| `sudo apt install openssh-server` | Install SSH server |
| `sudo systemctl start ssh` | Start SSH service |
| `sudo systemctl enable ssh` | Enable SSH on boot |
| `sudo systemctl status ssh` | Check SSH service status |
| `scp file user@ip:/path` | Copy file to remote VM |
| `cat file.txt` | Display file content |
| `ls` | List files in directory |

## Key Concepts Learned

### SSH (Secure Shell)
- Cryptographic network protocol for secure communication
- Used for remote login and command execution
- Default port: 22
- Uses encryption for secure data transfer

### SCP (Secure Copy Protocol)
- Uses SSH for authentication and encryption
- Command syntax: `scp source destination`
- Transfers files securely between machines
- Preserves file permissions during transfer

### VM Cloning
- Creates identical copy of virtual machine
- Two types:
  - **Linked Clone**: Shares virtual disks with parent VM, uses less disk space
  - **Full Clone**: Independent copy with own disks, uses more space
- Useful for testing, backups, and creating multiple environments

### Network Modes in VMware
- **NAT**: VMs share host's IP, isolated virtual network (used in this task)
- **Bridged**: VMs get separate IP on physical network
- **Host-Only**: VMs communicate only with host, no internet

### Use Cases in Cloud Computing
- **VM Migration**: Moving VMs between physical hosts
- **Data Backup**: Copying data to backup servers
- **Log Collection**: Gathering logs from multiple VMs
- **Software Distribution**: Deploying updates across VMs
- **Configuration Deployment**: Pushing configs to multiple servers

## Challenges Faced & Solutions

### Challenge 1: Bash Quote Error
**Problem:** Terminal showed `dquote>` prompt when using apostrophe 
in echo command (e.g., "Hifza's file").

**Solution:** Used simple text without apostrophes or escape characters. 
Bash was confused by mixing single and double quotes.

### Challenge 2: SSH Service Not Running Initially
**Problem:** SCP failed initially because SSH server was not installed 
by default on cloned VM.

**Solution:** Installed OpenSSH server using apt and started the service 
using systemctl.

### Challenge 3: First-Time Host Authentication
**Problem:** SCP asked for host authenticity confirmation.

**Solution:** Typed "yes" to add the host to known hosts list. This 
happens only on first connection.
