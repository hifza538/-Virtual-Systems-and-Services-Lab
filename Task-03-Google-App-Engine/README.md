
# Task 03: Google App Engine (GAE)

## Objective
To install and configure Google App Engine environment on Kali Linux 
Virtual Machine. Create a "Hello World" web application using Python 
Flask framework and run it on local development server.

## Tools Used
- Kali Linux (VMware VM)
- Python 3
- pip (Python Package Manager)
- Virtual Environment (venv)
- Flask Framework
- Gunicorn (WSGI Server)
- Firefox Browser

## Steps Performed

### Step 1: System Update
Updated the package list before installing new software.

Command: `sudo apt update`

<img width="586" height="157" alt="image" src="https://github.com/user-attachments/assets/d64e80e5-e3ab-4172-b2ad-e01a545be405" />


### Step 2: Python Version Verified
Python is pre-installed in Kali Linux. Verified version.

Command: `python3 --version`

<img width="1280" height="800" alt="Kali linux-2026-08-10-17-49-29" src="https://github.com/user-attachments/assets/c8303adf-4f70-47b2-a758-be0bf7d9c610" />


### Step 3: pip Installation
Installed pip (Python's package installer) to install Flask and other packages.

Command: `sudo apt install python3-pip -y`

<img width="1280" height="800" alt="Kali linux-2026-08-10-17-50-17" src="https://github.com/user-attachments/assets/88bd06cb-a14c-486a-be59-781101f192a7" />


### Step 4: pip Version Verified
Command: `pip3 --version`

<img width="1280" height="800" alt="Kali linux-2026-08-10-17-51-07" src="https://github.com/user-attachments/assets/6bdcfd8c-91e0-408f-a854-167e4bd2b035" />



### Step 5: Virtual Environment Setup
Created an isolated Python environment for the project to avoid 
conflicts with system packages.

Commands:
​```bash
sudo apt install python3-venv -y
mkdir ~/GAE-Project
cd ~/GAE-Project
python3 -m venv myenv
source myenv/bin/activate
​```

After activation, terminal prompt shows `(myenv)` prefix.

<img width="1280" height="800" alt="Kali linux-2026-08-10-17-54-57" src="https://github.com/user-attachments/assets/c7fc781e-a960-4260-b10f-bdb781b3b9fa" />


### Step 6: Flask & Gunicorn Installation
Installed Flask web framework and Gunicorn WSGI server.

Commands:
​```bash
pip install flask
pip install gunicorn
​```

<img width="1280" height="800" alt="Kali linux-2026-08-10-17-55-50" src="https://github.com/user-attachments/assets/4866c71d-02f0-44a5-bf0a-4335ad633b79" />


### Step 7: Flask Version Verified
Command: `pip show flask`

<img width="1280" height="800" alt="Kali linux-2026-08-10-17-57-19" src="https://github.com/user-attachments/assets/2df476cf-5616-4f4d-90f3-0949eef93db2" />


### Step 8: Application Code Created (main.py)
Created the main Flask application with two routes: home (`/`) 
and about (`/about`).

Command: `nano main.py`

<img width="578" height="229" alt="image" src="https://github.com/user-attachments/assets/740e1474-0ffb-413d-aacf-df33f7d1d97c" />


Save the file using: `Ctrl + O`, `Enter`, `Ctrl + X`

<img width="1280" height="800" alt="Kali linux-2026-08-10-17-58-39" src="https://github.com/user-attachments/assets/b799421d-692b-4b5c-88cf-fe902781ece1" />


### Step 9: GAE Configuration File (app.yaml)
Created the app.yaml file which tells Google App Engine how to 
run the application (runtime, entrypoint, etc).

Command: `nano app.yaml`

Code:
​```yaml
runtime: python39

entrypoint: gunicorn -b :$PORT main:app

handlers:
- url: /.*
  script: auto
​```
<img width="1280" height="800" alt="Kali linux-2026-08-10-18-00-28" src="https://github.com/user-attachments/assets/574c591e-31a2-4b48-a9c8-665c9a331824" />



### Step 10: Dependencies File (requirements.txt)
Created requirements.txt listing all Python packages needed.
GAE reads this file and installs dependencies automatically.

Command: `nano requirements.txt`

Content:
​```
Flask==2.3.0
gunicorn==21.2.0
​```

<img width="1280" height="800" alt="Kali linux-2026-08-10-18-01-51" src="https://github.com/user-attachments/assets/b1809a78-eedc-4d94-ac4f-6518a14fcf08" />


### Step 11: Project Files Verified
Command: `ls -l`

Confirmed all files are in place:
- main.py
- app.yaml
- requirements.txt
- myenv/ (virtual environment folder)

<img width="1280" height="800" alt="Kali linux-2026-08-10-18-02-26" src="https://github.com/user-attachments/assets/6583b8d6-8017-4401-b122-08309661da3d" />


### Step 12: Flask Application Executed
Started the Flask development server.

Command: `python3 main.py`

Output shows server is running on:
- http://127.0.0.1:8080
- http://192.168.100.82:8080

<img width="1280" height="800" alt="Kali linux-2026-08-10-18-03-08" src="https://github.com/user-attachments/assets/5729ee66-b2d2-4d38-b5c4-63c43c238e1a" />


### Step 13: Application Tested in Browser
Opened Firefox browser and visited the local server URL.

URL: `http://localhost:8080`

The Hello World page was successfully displayed with custom styling.

<img width="1280" height="800" alt="Kali linux-2026-08-10-18-08-51" src="https://github.com/user-attachments/assets/520a37b8-4f3b-4dd4-a4fa-44b3e93f5d4e" />


### Step 14: About Route Tested
URL: `http://localhost:8080/about`

The About page was successfully loaded.

<img width="1280" height="800" alt="Kali linux-2026-08-10-18-09-36" src="https://github.com/user-attachments/assets/e46cb05f-d8af-4886-a4de-f814102e8b0d" />


### Step 15: Server Stopped
Terminated the Flask server using: `Ctrl + C`

<img width="1280" height="800" alt="Kali linux-2026-08-10-18-10-56" src="https://github.com/user-attachments/assets/95f17960-cbf5-4d8a-b916-d83b8a5183b4" />


## Conclusion
Successfully installed and configured Google App Engine development 
environment on Kali Linux. Created a Python Flask web application with 
multiple routes, configured it with app.yaml for GAE deployment, and 
tested it on local development server. This demonstrates the concept 
of PaaS (Platform as a Service) where developers focus on code while 
the platform handles infrastructure.

## Commands Reference
| Command | Purpose |
|---------|---------|
| `sudo apt update` | Update package list |
| `sudo apt install python3-pip -y` | Install pip |
| `sudo apt install python3-venv -y` | Install venv module |
| `python3 -m venv myenv` | Create virtual environment |
| `source myenv/bin/activate` | Activate virtual environment |
| `pip install flask` | Install Flask framework |
| `pip install gunicorn` | Install Gunicorn server |
| `nano filename` | Create/edit file |
| `python3 main.py` | Run Flask application |
| `Ctrl + C` | Stop the server |
| `deactivate` | Exit virtual environment |

## Key Concepts Learned

### PaaS (Platform as a Service)
Google App Engine is a PaaS offering where developers upload their 
code and the platform automatically handles:
- Server provisioning
- Load balancing
- Auto-scaling
- Runtime environment

### Flask Framework
A lightweight Python web framework that allows quick development 
of web applications using minimal code.

### app.yaml
Configuration file specific to Google App Engine that defines:
- Runtime (Python version)
- Entry point (how to start the app)
- URL handlers and routing

### Virtual Environment
Isolated Python environment that keeps project dependencies 
separate from system-wide Python packages.

### Cloud Service Models
- **IaaS**: Infrastructure as a Service (AWS EC2, Azure VM)
- **PaaS**: Platform as a Service (Google App Engine, Heroku)
- **SaaS**: Software as a Service (Gmail, Google Docs)
