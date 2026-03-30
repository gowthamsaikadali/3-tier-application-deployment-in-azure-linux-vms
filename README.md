🚀 3-Tier Application Deployment (Flask + MySQL)
📌 Project Overview
This project demonstrates the deployment of a 3-tier architecture by separating the application into:

Web Server (Frontend) – Flask UI (Port 5000)
App Server (Backend) – Flask API + SQLAlchemy + JWT (Port 5001)
DB Server (Database) – MySQL (Port 3306)
This architecture improves scalability, security, and maintainability.

🎯 Aim
To design and deploy a scalable 3-tier application with proper communication between frontend, backend, and database layers.

🛠️ Tech Stack
Python (Flask)
MySQL
SQLAlchemy
Linux (Ubuntu)
Virtual Machines (Cloud)
⚙️ Setup Instructions
🔹 1. Database Server (MySQL)
sudo apt update
sudo apt install mysql-server -y
sudo systemctl start mysql
➡️ Install and start MySQL

CREATE DATABASE appdb;
CREATE USER 'appuser'@'%' IDENTIFIED BY 'Password12345';
GRANT ALL PRIVILEGES ON appdb.* TO 'appuser'@'%';
FLUSH PRIVILEGES;
➡️ Create database and user

🔹 2. App Server (Backend)
git clone https://github.com/gowthamsaikadali/vcube-3tier-application-python.git
cd Vcube_App/app_server
➡️ Clone backend code

python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
pip install mysqlclient
➡️ Setup environment and dependencies

export DATABASE_URL="mysql://appuser:Password12345@<DB_IP>/appdb"
export APP_HOST="0.0.0.0"
export APP_PORT=5001
➡️ Configure backend

nohup python3 app.py &
➡️ Run backend server

🔹 3. Web Server (Frontend)
git clone https://github.com/gowthamsaikadali/vcube-3tier-application-python.git
cd Vcube_App/web_server
➡️ Clone frontend code

python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
➡️ Setup environment

export APP_INTERNAL="http://<APP_IP>:5001"
export WEB_PORT=5000
➡️ Configure frontend

nohup python3 app.py &
➡️ Run frontend server

🌐 Access Application
Open in browser:

http://<WEB_PUBLIC_IP>:5000
🔄 Request Flow
User → Web Server → App Server → DB Server

🔐 Ports Used
5000 → Web Server
5001 → App Server
3306 → MySQL
22 → SSH
🧪 Testing
curl http://<APP_IP>:5001/api/health
Expected:

{"status": "ok"}
✅ Conclusion
This project demonstrates the successful deployment of a 3-tier application with improved scalability and security. It provided hands-on experience in application deployment, backend integration, and troubleshooting.

👨‍💻 Author
Gowtham Sai
