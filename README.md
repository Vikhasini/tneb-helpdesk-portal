A full-stack web application built for the Tamil Nadu Electricity Board (TNEB) to streamline official email support and IT helpdesk operations.

The portal enables employees to raise support requests, request official email IDs, reset forgotten passwords, and track tickets through a chatbot-first interface. Administrators can manage requests, update ticket statuses, approve email/password requests, and monitor system activity through a centralized dashboard.

🔗 Live Demo: https://chatbot-tneb.onrender.com/

📂 GitHub Repository: https://github.com/Vikhasini/tneb-helpdesk-portal

📌 Features
🌐 Public Portal
AI-style rule-based support chatbot
Track support tickets using Ticket ID
Submit password reset requests
Request official TNEB email IDs
Frequently Asked Questions (FAQ)
👨‍💼 Employee Portal
Secure employee login
Dashboard with announcements and recent tickets
Raise support tickets with category and priority
View ticket history and admin responses
Chat-based support assistant
👨‍💻 Admin Portal
Dashboard with live statistics and analytics
Manage support tickets
Assign tickets and update status
Add public and internal notes
Approve password reset requests
Approve official email ID requests
Real-time notification center
Employee directory management
🔒 Security Features
Custom arithmetic CAPTCHA (No Google reCAPTCHA)
Session-based authentication using Flask-Login
PBKDF2-SHA256 password hashing
CSRF protection using Flask-WTF
Role-Based Access Control
Public
Employee
Admin
Super Admin
🛠 Tech Stack
Category	Technology
Backend	Python, Flask
Frontend	HTML, CSS, Bootstrap 5, JavaScript
Database	PostgreSQL
ORM	SQLAlchemy
Authentication	Flask-Login
Security	Flask-WTF, PBKDF2 Password Hashing
Charts	Chart.js
Deployment	Render
Version Control	Git & GitHub
🏗 System Architecture
User
   │
   ▼
Browser
   │
   ▼
Flask Application
   │
   ├──────── Authentication
   ├──────── Chatbot
   ├──────── Ticket Management
   ├──────── Employee Module
   ├──────── Admin Module
   │
   ▼
PostgreSQL Database
📂 Project Structure
tneb-helpdesk-portal/
│
├── app/
│   ├── blueprints/
│   │   ├── admin/
│   │   ├── auth/
│   │   ├── chatbot/
│   │   ├── employee/
│   │   ├── notifications/
│   │   ├── public/
│   │   └── tickets/
│   │
│   ├── models/
│   ├── static/
│   ├── templates/
│   ├── utils.py
│   └── __init__.py
│
├── seed/
├── config.py
├── run.py
├── requirements.txt
└── README.md
⚙ Installation
1. Clone the Repository
git clone https://github.com/Vikhasini/tneb-helpdesk-portal.git
cd tneb-helpdesk-portal
2. Create Virtual Environment
python -m venv venv

Activate it

Windows

venv\Scripts\activate

Mac/Linux

source venv/bin/activate
3. Install Dependencies
pip install -r requirements.txt
4. Configure Environment Variables

Create a .env file.

DATABASE_URL=your_postgresql_database_url
SECRET_KEY=your_secret_key
FLASK_ENV=development
5. Run the Application
python run.py

Open

http://localhost:5000
🚀 Deployment

The project is deployed on Render.

Deployment includes:

Flask Application
PostgreSQL Database
Gunicorn
Environment Variables
Automatic Database Initialization
👥 Default Demo Credentials
Super Admin
Username : admin
Password : admin123
Admin
Username : admin01
Password : Admin@1234
Employee
Username : EMP001
Password : Tneb@1234

Note: These credentials are provided only for demonstration purposes.

🗄 Database Models
User
Employee
OfficialEmail
SupportTicket
PasswordResetRequest
EmailRequest
Notification
ChatbotLog
🔄 Application Workflow
Public User / Employee
            │
            ▼
      Login / Chatbot
            │
            ▼
   Submit Request / Raise Ticket
            │
            ▼
     Stored in PostgreSQL
            │
            ▼
 Admin Reviews the Request
            │
            ▼
 Approve / Reject / Update Status
            │
            ▼
 User Receives Updated Response
🎯 Key Highlights
Full-stack Flask application
Modular Blueprint Architecture
PostgreSQL integration using SQLAlchemy
Secure authentication and authorization
Chatbot-assisted support workflow
Ticket lifecycle management
Admin approval system
Responsive Bootstrap interface
Cloud deployment using Render
📚 Future Enhancements
Email notifications using SMTP
OTP-based password recovery
AI-powered chatbot integration
File attachments for support tickets
Analytics dashboard with advanced reporting
Mobile-responsive PWA version
👩‍💻 Developer

Vikhasini S

B.Tech – Information and Communication Technology

Passionate about Full Stack Development, Data Analytics, and building scalable software solutions.
