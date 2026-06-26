# TNEB Digital Helpdesk & Official Email Support Portal

A production-ready government employee self-service portal built for Tamil Nadu Electricity Board (TNEB). Employees and the public can report email issues, request official email IDs, reset passwords, and track support tickets — all through a chatbot-first interface. Deployed on Render with PostgreSQL.

---

## Features

### Public (No Login Required)
- AI-style rule-based support chatbot
- Ticket tracking by ticket ID
- Forgot password request form
- Official email ID request form
- FAQ page

### Employee
- Dashboard with recent tickets and announcements
- Raise support tickets (category, priority, description)
- View full ticket history with admin replies
- Chat support assistant

### Admin
- Dashboard with live statistics and Chart.js analytics
- Ticket management — assign, update status, add public/internal notes
- Password reset request approvals — generates temporary password on approval
- Official email request approvals — assign email address on approval
- Real-time notification center
- Employee directory

### Security
- Arithmetic CAPTCHA on every login (no third-party service)
- Session-based authentication via Flask-Login
- PBKDF2-SHA256 password hashing via Werkzeug
- CSRF protection on all forms via Flask-WTF
- Role-based access control (public / employee / admin / superadmin)

---

## Tech Stack

| Layer | Technology |
|---|---|
| Backend | Python 3.11+, Flask 3.0 |
| ORM | Flask-SQLAlchemy 3.1 |
| Auth | Flask-Login 0.6 |
| Database | PostgreSQL (Render managed) |
| DB Driver | psycopg v3 — Python 3.14 compatible |
| WSGI | Gunicorn |
| Frontend | Bootstrap 5.3, Vanilla JS, Chart.js 4 |
| Deployment | Render Free Tier |

---

## Project Structure

```
tneb_portal/
├── run.py                        # Gunicorn entry point
├── config.py                     # PostgreSQL config, Render URL fix, pool settings
├── requirements.txt
├── .env.example
├── seed/seed_data.py             # Manual re-seed script (local dev only)
└── app/
    ├── __init__.py               # App factory + auto DB init + seeding
    ├── models/__init__.py        # 8 SQLAlchemy models
    ├── utils.py                  # Shared helpers (notifications, ticket IDs)
    ├── blueprints/
    │   ├── public/               # /, /helpdesk, /track, /faq, /forgot-password, /request-email
    │   ├── auth/                 # /auth/login, /auth/logout, /auth/forgot-password
    │   ├── employee/             # /employee/dashboard, /raise-ticket, /tickets
    │   ├── admin/                # /admin/dashboard, /tickets, /password-requests,
    │   │                         #   /email-requests, /employees, /notifications
    │   ├── chatbot/              # /chatbot/support, /chatbot/message (AJAX API)
    │   ├── tickets/              # /tickets/track, /tickets/search (AJAX API)
    │   └── notifications/        # /notifications/*, unread count API
    ├── static/
    │   ├── css/portal.css
    │   └── js/{portal,chatbot}.js
    └── templates/                # 23 Jinja2 templates across 6 folders
```

---

## Local Setup

### Prerequisites
- Python 3.11+
- PostgreSQL 14+

### Steps

```bash
# 1. Clone
git clone https://github.com/YOU/tneb-portal.git
cd tneb-portal

# 2. Virtual environment
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Create the database
createdb tneb_portal

# 5. Configure environment
cp .env.example .env
# Edit .env — set DATABASE_URL and SECRET_KEY
```

**.env**
```env
DATABASE_URL=postgresql://postgres:YOUR_PASSWORD@localhost/tneb_portal
SECRET_KEY=any-long-random-string
FLASK_ENV=development
```

```bash
# 6. Run
python run.py
```

Tables and seed data are created automatically on first run. Open **http://localhost:5000**.

---

## Default Credentials

| Role | Username | Password |
|---|---|---|
| Superadmin | `admin` | `admin123` |
| Admin | `admin01` – `admin09` | `Admin@1234` |
| Superadmin | `admin10` | `Admin@1234` |
| Employee | `EMP001` – `EMP020` | `Tneb@1234` |

> Change all passwords immediately in any non-demo environment.

---

## Deploy to Render

### 1. Create a PostgreSQL database on Render
Render Dashboard → **New +** → **PostgreSQL** → Free → Create

Copy the **Internal Database URL**.

### 2. Create a Web Service
Render Dashboard → **New +** → **Web Service** → connect your GitHub repo

| Setting | Value |
|---|---|
| Runtime | Python 3 |
| Build Command | `pip install -r requirements.txt` |
| Start Command | `gunicorn run:app` |
| Plan | Free |

### 3. Set Environment Variables

| Key | Value |
|---|---|
| `DATABASE_URL` | Internal Database URL from step 1 |
| `SECRET_KEY` | Any long random string |

### 4. Deploy

Click **Manual Deploy → Deploy latest commit**.

On first boot the app automatically:
1. Creates all PostgreSQL tables
2. Seeds admin accounts
3. Seeds 50 employees, 100 tickets, sample data

No shell access or manual migration required.

---

## Page Reference

| URL | Description | Access |
|---|---|---|
| `/` | Public home | Public |
| `/helpdesk` | Support chatbot | Public |
| `/track` | Ticket tracker | Public |
| `/faq` | FAQ | Public |
| `/forgot-password` | Password reset request | Public |
| `/request-email` | Official email request | Public |
| `/auth/login` | Login | Public |
| `/employee/dashboard` | Employee home | Employee |
| `/employee/raise-ticket` | New ticket | Employee |
| `/employee/tickets` | Ticket history | Employee |
| `/chatbot/support` | Chat assistant | Employee |
| `/admin/dashboard` | Admin overview | Admin |
| `/admin/tickets` | Ticket management | Admin |
| `/admin/password-requests` | Password reset approvals | Admin |
| `/admin/email-requests` | Email ID approvals | Admin |
| `/admin/employees` | Employee directory | Admin |
| `/admin/notifications` | Notification center | Admin |
| `/health` | Health check (Render) | Public |

---

## Database Models

| Model | Purpose |
|---|---|
| `Employee` | HR data — name, designation, office, district |
| `OfficialEmail` | Assigned TNEB email addresses |
| `User` | Authentication — username, password hash, role |
| `SupportTicket` | Issue tickets with status lifecycle |
| `PasswordResetRequest` | Admin-approved password resets |
| `EmailRequest` | Admin-approved email provisioning requests |
| `Notification` | Admin notification feed |
| `ChatbotLog` | Audit log of all chatbot conversations |

---

## Environment Variables

| Variable | Required | Description |
|---|---|---|
| `DATABASE_URL` | ✅ | PostgreSQL connection string |
| `SECRET_KEY` | ✅ | Flask session signing key |
| `FLASK_ENV` | Optional | `development` or `production` (default: `production`) |

---

## License

Internal government use — Tamil Nadu Electricity Board © 2025
