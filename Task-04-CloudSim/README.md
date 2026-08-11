
# Task 04: CloudSim - Cloud Computing Simulation

## Objective
To install and configure CloudSim framework on Kali Linux Virtual Machine. 
Simulate a cloud scenario with datacenters, virtual machines, and cloudlets 
(tasks). Run both built-in and custom simulation programs to demonstrate 
cloud resource management and task scheduling.

## Tools Used
- Kali Linux (VMware VM)
- Java JDK 21 (OpenJDK)
- Maven Build Tool
- CloudSim 4.0 Framework
- ZSH Shell (Kali default)

## What is CloudSim?
CloudSim is a Java-based simulation framework that enables modeling and 
simulation of cloud computing environments. It allows developers and 
researchers to test scheduling algorithms, resource allocation, and 
performance analysis without needing actual cloud infrastructure like 
AWS or Azure.

## Steps Performed

### Step 1: System Update
Updated the package list before installing new software.

Command: `sudo apt update`

<img width="1280" height="800" alt="Kali linux-2026-08-10-20-02-44" src="https://github.com/user-attachments/assets/7efb8cfd-ac9c-46c1-b1d8-8a8ae432dcc3" />


### Step 2: Java JDK Installation
Installed Java Development Kit which is required to run CloudSim.

Command: `sudo apt install default-jdk -y`

<img width="1280" height="800" alt="Kali linux-2026-08-10-20-04-44" src="https://github.com/user-attachments/assets/8e40abb3-3199-4fd6-a3b7-5af5ef637642" />


### Step 3: Java Version Verified
Command: `java --version`

Multiple Java versions were found (Java 21, 25). Java 21 was chosen 
as it is a stable LTS version.

<img width="1280" height="800" alt="Kali linux-2026-08-10-20-51-29" src="https://github.com/user-attachments/assets/5a71565c-1df5-453d-b3fc-f16582cdb766" />


### Step 4: Working Directory Created
Created a dedicated folder for CloudSim project.

Commands:

    mkdir ~/CloudSim-Project
    cd ~/CloudSim-Project

<img width="1280" height="800" alt="Kali linux-2026-08-10-20-53-24" src="https://github.com/user-attachments/assets/3fabac7c-cb20-4a5e-9d2c-29f1d7cea9af" />


### Step 5: CloudSim Downloaded
Downloaded CloudSim 4.0 source code from the official GitHub repository.

Command:

    wget https://github.com/Cloudslab/cloudsim/archive/refs/tags/cloudsim-4.0.tar.gz

<img width="1280" height="800" alt="Kali linux-2026-08-10-20-54-01" src="https://github.com/user-attachments/assets/0e854f8c-ec2b-4983-9ce3-030669e8a195" />


### Step 6: Archive Extracted
Extracted the downloaded tar.gz file.

Command: `tar -xvzf cloudsim-4.0.tar.gz`
show file: `ls`

<img width="1280" height="800" alt="Kali linux-2026-08-10-21-06-47" src="https://github.com/user-attachments/assets/488bcb2a-a17d-4f75-baaa-687d15fc5f06" />



### Step 7: Folder Renamed
Renamed the long folder name to a simpler one for easy access.

Commands:

    mv cloudsim-cloudsim-4.0 cloudsim
    cd cloudsim
    ls

Contents: distribution, documentation, modules, pom.xml, README.md

<img width="1280" height="800" alt="Kali linux-2026-08-10-21-11-11" src="https://github.com/user-attachments/assets/0cef85fa-e23c-48b9-a29a-50b91e9399af" />


### Step 8: Maven Installation
Installed Apache Maven build tool required to build CloudSim project.

Command: `sudo apt install maven -y`

<img width="1280" height="800" alt="Kali linux-2026-08-11-10-18-08" src="https://github.com/user-attachments/assets/9488527a-e988-4c4e-bb2e-583a803c1266" />


### Step 9: Maven Version Verified
Command: `mvn --version`

<img width="1280" height="800" alt="Kali linux-2026-08-11-10-21-06" src="https://github.com/user-attachments/assets/7ec3cad8-c58c-4826-b237-4d7265ba655a" />


### Step 10: JAVA_HOME Environment Variable Set
Since Kali Linux uses ZSH shell by default, added Java environment 
variables to `~/.zshrc` file (not `.bashrc`).

Commands:

    nano ~/.zshrc

Added at end of file:

    export JAVA_HOME=/usr/lib/jvm/java-21-openjdk-amd64
    export PATH=$JAVA_HOME/bin:$PATH

Applied changes: `source ~/.zshrc`

Verified: `echo $JAVA_HOME`

<img width="1280" height="800" alt="Kali linux-2026-08-11-10-50-54" src="https://github.com/user-attachments/assets/956cab55-dac2-440a-b75c-25253c438ae4" />


### Step 11: CloudSim Built with Maven
Built the CloudSim project skipping tests and javadoc generation.

Command:

    cd ~/CloudSim-Project/cloudsim
    mvn clean package -DskipTests -Dmaven.javadoc.skip=true

Result: BUILD SUCCESS - JAR files were generated in target folders.

<img width="1280" height="800" alt="Kali linux-2026-08-11-11-01-34" src="https://github.com/user-attachments/assets/acca3c97-f7e5-4fe0-a649-90c542f28187" />


### Step 12: JAR Files Verified
Command:

    find ~/CloudSim-Project -name "cloudsim*.jar"

JAR files found:
- cloudsim-4.0.jar
- cloudsim-examples-4.0.jar

<img width="1280" height="800" alt="Kali linux-2026-08-11-11-02-28" src="https://github.com/user-attachments/assets/bb4312b0-acc5-4d9f-8e2c-e4cd50ffd908" />


### Step 13: Built-in Sample Example Executed
Ran the CloudSimExample1 to test the installation.

Commands:

    cd ~/CloudSim-Project/cloudsim/modules/cloudsim-examples
    java -cp "target/cloudsim-examples-4.0.jar:../cloudsim/target/cloudsim-4.0.jar" org.cloudbus.cloudsim.examples.CloudSimExample1

Output:
- Datacenter_0 created successfully
- VM #0 created and allocated
- Cloudlet 0 executed successfully  
- Status: SUCCESS
- Execution Time: 400 seconds

<img width="1280" height="800" alt="Kali linux-2026-08-11-11-05-13" src="https://github.com/user-attachments/assets/afb1cb7d-5d87-4a00-99dc-93e5579c27cb" />


### Step 14: Custom Program Created (MyCloudSimExample.java)
Created a custom CloudSim simulation program with:
- 1 Datacenter
- 2 Virtual Machines
- 4 Cloudlets (Tasks)

Command:

    cd ~/CloudSim-Project/cloudsim/modules/cloudsim-examples/src/main/java/org/cloudbus/cloudsim/examples/
    nano MyCloudSimExample.java

Custom Code Features:
- Creates multiple VMs to test load distribution
- Runs multiple cloudlets to test scheduling
- Uses Time-Shared scheduling algorithm
- Displays detailed execution results

<img width="599" height="213" alt="image" src="https://github.com/user-attachments/assets/df40b250-3a5e-41c6-b478-47cc86735b6f" />


### Step 15: Custom Program Compiled
Command:

    cd ~/CloudSim-Project/cloudsim/modules/cloudsim-examples
    javac --release 21 -cp "target/cloudsim-examples-4.0.jar:../cloudsim/target/cloudsim-4.0.jar" -d target/classes src/main/java/org/cloudbus/cloudsim/examples/MyCloudSimExample.java

Note: Used `--release 21` flag to ensure Java version compatibility.


### Step 16: Custom Program Executed
Command:

    java -cp "target/classes:../cloudsim/target/cloudsim-4.0.jar" org.cloudbus.cloudsim.examples.MyCloudSimExample

Output showed:
- 2 VMs created successfully
- 4 Cloudlets distributed across VMs
- All tasks completed with SUCCESS status
- Execution details for each cloudlet displayed

<img width="1280" height="800" alt="Kali linux-2026-08-11-11-22-07" src="https://github.com/user-attachments/assets/ddc753df-f95b-4b28-8940-95288ac7afdc" />


## Conclusion
Successfully installed and configured CloudSim framework on Kali Linux. 
Overcame challenges including Java version conflicts (used --release 21), 
ZSH vs BASH shell differences (used .zshrc), and Maven build issues 
(skipped javadoc). Simulated cloud computing environments with both 
built-in and custom programs, demonstrating datacenters, virtual machines, 
cloudlets, and task scheduling. This proves that CloudSim can be used 
to test cloud algorithms without actual cloud infrastructure.

## Commands Reference

| Command | Purpose |
|---------|---------|
| `sudo apt install default-jdk -y` | Install Java JDK |
| `sudo apt install maven -y` | Install Maven build tool |
| `export JAVA_HOME=path` | Set Java environment variable |
| `source ~/.zshrc` | Apply zsh config changes |
| `mvn clean package -DskipTests` | Build project skipping tests |
| `javac --release 21 -cp jars file.java` | Compile with Java 21 target |
| `java -cp jars ClassName` | Run Java program with classpath |
| `find . -name "*.jar"` | Find JAR files |

## Key Concepts Learned

### CloudSim Components:
- **Datacenter**: Physical infrastructure that hosts multiple hosts
- **Host**: Physical server with CPU (PEs), RAM, Storage, Bandwidth
- **VM (Virtual Machine)**: Virtualized computing resource running on host
- **Cloudlet**: Task or job to be executed on a VM
- **Broker**: Middleware that manages VMs and Cloudlets on user's behalf
- **CIS (Cloud Information Service)**: Registry of all cloud resources

### Scheduling Algorithms:
- **Time-Shared Scheduling**: Multiple cloudlets share VM time slots 
  (used in our simulation)
- **Space-Shared Scheduling**: Cloudlets execute one after another 
  with dedicated resources

### Simulation Flow:
1. Initialize CloudSim
2. Create Datacenter with Hosts
3. Create Broker
4. Create VMs and submit to Broker
5. Create Cloudlets and submit to Broker
6. Start Simulation
7. Collect and Display Results
8. Stop Simulation

### Cloud Service Models:
- **IaaS**: Infrastructure as a Service (what CloudSim simulates)
- **PaaS**: Platform as a Service
- **SaaS**: Software as a Service

### Why CloudSim?
- **Free and open-source** - No cost
- **No physical infrastructure needed** - Just Java
- **Fast experimentation** - Test many scenarios quickly  
- **Repeatable results** - Same input = same output
- **Research friendly** - Widely used in academic papers
- **Extensible** - Can add custom algorithms

## Challenges Faced & Solutions

### Challenge 1: JAVA_HOME not set
**Error:** `Unable to find javadoc command: JAVA_HOME not correctly set`

**Solution:** Set JAVA_HOME in `.zshrc` (not `.bashrc` because Kali 
uses ZSH shell).

### Challenge 2: Maven Build Failure
**Error:** Javadoc plugin failure

**Solution:** Added `-Dmaven.javadoc.skip=true` flag to skip 
documentation generation.

### Challenge 3: Java Version Mismatch
**Error:** `UnsupportedClassVersionError: class file version 69.0`

**Solution:** Used `--release 21` flag during compilation to generate 
bytecode compatible with Java 21 runtime.

### Challenge 4: Corrupt .bashrc
**Problem:** Terminal showed strange characters after adding env variables.

**Solution:** Realized Kali uses ZSH not BASH, so used `.zshrc` file 
instead, which resolved the issue.
