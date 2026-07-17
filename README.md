# ⚡ TNEB Digital Helpdesk & Official Email Support Portal

A full-stack web application built for the **Tamil Nadu Electricity Board (TNEB)** to streamline official email support and IT helpdesk operations.

The portal enables employees to raise support requests, request official email IDs, reset forgotten passwords, and track tickets through a chatbot-first interface. Administrators can manage requests, update ticket statuses, approve email/password requests, and monitor system activity through a centralized dashboard.

🌐 **Live Demo:** https://chatbot-tneb.onrender.com/

💻 **GitHub Repository:** https://github.com/Vikhasini/tneb-helpdesk-portal

---

# 📌 Features

## 🌐 Public Portal

- AI-style rule-based support chatbot
- Track support tickets using Ticket ID
- Submit password reset requests
- Request official TNEB email IDs
- Frequently Asked Questions (FAQ)

---

## 👨‍💼 Employee Portal

- Secure employee login
- Dashboard with announcements and recent tickets
- Raise support tickets with category and priority
- View ticket history and admin responses
- Chat-based support assistant

---

## 👨‍💻 Admin Portal

- Dashboard with live statistics and analytics
- Manage support tickets
- Assign tickets and update status
- Add public and internal notes
- Approve password reset requests
- Approve official email ID requests
- Real-time notification center
- Employee directory management

---

# 🔒 Security Features

- Custom arithmetic CAPTCHA (No Google reCAPTCHA)
- Session-based authentication using Flask-Login
- PBKDF2-SHA256 password hashing
- CSRF protection using Flask-WTF
- Role-Based Access Control
  - Public
  - Employee
  - Admin
  - Super Admin

---

# 🛠 Tech Stack

| Category | Technology |
|----------|------------|
| **Backend** | Python, Flask |
| **Frontend** | HTML, CSS, Bootstrap 5, JavaScript |
| **Database** | PostgreSQL |
| **ORM** | SQLAlchemy |
| **Authentication** | Flask-Login |
| **Security** | Flask-WTF, PBKDF2 Password Hashing |
| **Charts** | Chart.js |
| **Deployment** | Render |
| **Version Control** | Git & GitHub |

---

# 🏗️ System Architecture

```text
                User
                  │
                  ▼
             Web Browser
                  │
                  ▼
         Flask Application
                  │
 ┌────────────────┼────────────────┐
 │                │                │
 ▼                ▼                ▼
Authentication  Chatbot     Ticket System
 │                │                │
 └────────────────┼────────────────┘
                  │
                  ▼
        PostgreSQL Database
```

---

# 📂 Project Structure

```text
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
```

---

# 🚀 Getting Started

## Prerequisites

- Python 3.11+
- PostgreSQL
- Git

---

## 1️⃣ Clone the Repository

```bash
git clone https://github.com/Vikhasini/tneb-helpdesk-portal.git
cd tneb-helpdesk-portal
```

---

## 2️⃣ Create a Virtual Environment

### Windows

```bash
python -m venv venv
venv\Scripts\activate
```

### macOS / Linux

```bash
python3 -m venv venv
source venv/bin/activate
```

---

## 3️⃣ Install Dependencies

```bash
pip install -r requirements.txt
```

---

## 4️⃣ Configure Environment Variables

Create a `.env` file in the project root.

```env
DATABASE_URL=your_postgresql_database_url
SECRET_KEY=your_secret_key
FLASK_ENV=development
```

---

## 5️⃣ Run the Application

```bash
python run.py
```

Open:

```
http://localhost:5000
```

---

# 🚀 Deploy on Render

## 1. Create PostgreSQL Database

- Go to Render Dashboard
- Create a PostgreSQL Database
- Copy the **Internal Database URL**

---

## 2. Create a Web Service

Connect your GitHub repository.

Use:

| Setting | Value |
|---------|-------|
| Runtime | Python |
| Build Command | `pip install -r requirements.txt` |
| Start Command | `gunicorn run:app` |

---

## 3. Environment Variables

| Variable | Value |
|-----------|-------|
| DATABASE_URL | Internal PostgreSQL URL |
| SECRET_KEY | Random Secret Key |

---

## 4. Deploy

Render automatically:

- Creates database tables
- Seeds demo data
- Starts Gunicorn
- Hosts the application

---

# 👥 Demo Credentials

## Super Admin

```
Username : admin
Password : admin123
```

---

## Admin

```
Username : admin01
Password : Admin@1234
```

---

## Employee

```
Username : EMP001
Password : Tneb@1234
```

> **Note:** These credentials are for demonstration purposes only.

---

# 🗄️ Database Models

- User
- Employee
- OfficialEmail
- SupportTicket
- PasswordResetRequest
- EmailRequest
- Notification
- ChatbotLog

---

# 🔄 Application Workflow

```text
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
```

---

# ✨ Key Highlights

- Full-stack Flask application
- Modular Blueprint Architecture
- PostgreSQL integration using SQLAlchemy
- Secure authentication & authorization
- Chatbot-assisted support workflow
- Ticket lifecycle management
- Admin approval system
- Responsive Bootstrap interface
- Cloud deployment using Render

---

# 🚀 Future Enhancements

- Email notifications (SMTP)
- OTP-based password recovery
- AI-powered chatbot integration
- File upload support for tickets
- Advanced analytics dashboard
- Progressive Web App (PWA)

---

# 👩‍💻 Developer

**Vikhasini M S**

**B.Tech – Information and Communication Technology**

Passionate about Full Stack Development, Data Analytics, and building scalable software solutions.

- 🌐 Live Demo: https://chatbot-tneb.onrender.com/
- 💻 GitHub: https://github.com/Vikhasini/tneb-helpdesk-portal


It is inspired by a real-world government helpdesk workflow and is **not an official Tamil Nadu Electricity Board (TNEB) application**.

© 2025 Vikhasini S. All Rights Reserved.
