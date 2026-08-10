
# Task 02: C Compiler Installation & Program Execution

## Objective
To install and configure GCC (GNU C Compiler) on Kali Linux 
Virtual Machine and execute C programs.

## Tools Used
- Kali Linux (VMware VM)
- GCC Compiler
- Nano Text Editor

## Steps Performed

### Step 1: Terminal Opened
open terminal using key: Ctrl + Alt + T
or click on terminal icon 

<img width="1280" height="800" alt="Kali linux-2026-08-10-15-57-27" src="https://github.com/user-attachments/assets/4c5221b1-b9b1-4298-8ff3-3a44b36b5844" />


### Step 2: System Updated
Command: `sudo apt update`

<img width="1280" height="800" alt="Kali linux-2026-08-10-16-05-25" src="https://github.com/user-attachments/assets/4c067587-307e-488b-900c-e1c9a775b34d" />


### Step 3: GCC Installation
Command: `sudo apt install gcc -y`

it takes some time

<img width="1280" height="800" alt="Kali linux-2026-08-10-16-11-00" src="https://github.com/user-attachments/assets/d90eb057-e292-459e-ae65-fed17ec94be2" />


### Step 4: GCC Version Verified
verify, is gcc successfully installed

Command: `gcc --version`

<img width="1280" height="800" alt="Kali linux-2026-08-10-16-11-56" src="https://github.com/user-attachments/assets/e24c54ca-6914-4f63-9a58-dcc2675a2236" />


### Step 5: Working Directory Created
make folder/directory where c programs will saved/stored

`mkdir ~/C-Programs`

`cd ~/C-Programs`

`pwd`

<img width="1280" height="800" alt="Kali linux-2026-08-10-16-18-21" src="https://github.com/user-attachments/assets/d96b0a8d-3bc2-4c2d-9841-6246320dd6fa" />

### Step 6: create file,write code
`nano hello.c`

write code/program

<img width="1280" height="800" alt="Kali linux-2026-08-10-16-23-14" src="https://github.com/user-attachments/assets/a04e225f-d30a-4b4d-a15d-4d9ffdc6ae93" />


ctrl+o to save

tap enter

ctrl+x to exit


### step 7: Compile and run
gcc hello.c -o hello

./hello

output is shown

<img width="1280" height="800" alt="Kali linux-2026-08-10-16-28-28" src="https://github.com/user-attachments/assets/9ad9cbce-c888-48f8-8a8a-5fa0c55b8b1b" />

#### Program 2: Sum
Create file using command `nano sum.c`

and write code 

<img width="1280" height="800" alt="Kali linux-2026-08-10-17-01-31" src="https://github.com/user-attachments/assets/7f0882ad-32ed-4f25-ae5d-9b85478e75bf" />

save file( ctrl+o , press enter, ctrl+x)

compile and run
gcc sum.c -o sum

./sum

<img width="1280" height="800" alt="Kali linux-2026-08-10-17-02-45" src="https://github.com/user-attachments/assets/a16e0313-3648-4ce4-99a8-1cb3d737de54" />

### list files with details
ls-l

<img width="1280" height="800" alt="Kali linux-2026-08-10-17-07-49" src="https://github.com/user-attachments/assets/571c48a1-5188-4130-a272-adc36320b0fe" />



## Conclusion
Successfully installed GCC compiler on Kali Linux VM and 
executed 2 C programs (Hello World and sum). 
Both programs compiled and ran successfully in virtual environment.

## Commands Reference
| Command | Purpose |
|---------|---------|
| `sudo apt update` | Update package list |
| `sudo apt install gcc -y` | Install GCC compiler |
| `gcc --version` | Check GCC version |
| `mkdir ~/C-Programs` | Create directory |
| `nano file.c` | Create/edit file |
| `gcc file.c -o output` | Compile C program |
| `./output` | Run compiled program |
| `ls -l` | List files with details |

