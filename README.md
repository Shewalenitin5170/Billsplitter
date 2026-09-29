# Billsplitter
BillSplitter — A full-stack expense splitting web app built with Python (Flask), SQLite, and JavaScript (React)

# BillSplitter

A full-stack expense splitting web application that helps groups of friends, 
family, or colleagues track and split shared expenses fairly.

## Features

-  User Authentication (Register/Login with JWT)
-  Create Groups with unique invite codes
-  Join groups using 6-character group code
-  Add expenses and split them among members
-  Real-time balance tracking (who owes whom)
-  Settle Up — clear breakdown of payments with + and - 
-  Transaction History across all groups
-  Dark / Light mode
-  Delete groups with full history cleanup

##  Tech Stack

### Backend
| Technology | Purpose |
|---|---|
| Python 3 | Core backend language |
| Flask | REST API framework |
| SQLite | Database |
| JWT (PyJWT) | Authentication tokens |
| Werkzeug | Password hashing |
| Flask-CORS | Cross-origin requests |

### Frontend
| Technology | Purpose |
|---|---|
| HTML5 | Structure |
| CSS3 | Styling with dark/light theme |
| JavaScript (ES6+) | Logic |
| React 18 | UI components |
| Fetch API | Backend communication |

##  Project Structure

\`\`\`
billsplitter/
│
├── backend/
│   ├── app.py               ← Flask server + all API routes
│   ├── database.py          ← SQLite setup + 5 tables
│   ├── auth.py              ← Register, Login, JWT tokens
│   ├── groups.py            ← Group CRUD operations
│   ├── transactions.py      ← Expenses + Settle Up logic
│   └── requirements.txt     ← Python dependencies
│
└── frontend/
    ├── index.html           ← Entry point
    ├── css/
    │   └── style.css        ← All styles
    └── js/
        ├── api.js           ← All fetch() calls to backend
        ├── utils.js         ← Icons, formatters, settlement algorithm
        ├── app.js           ← App root, Auth, Sidebar, Topbar
        ├── dashboard.js     ← Dashboard + Groups list
        ├── groups_ui.js     ← Create Group, Group Detail, Expense Modal
        └── history.js       ← Join Group, History Page, App Mount
\`\`\`

## Database Schema

\`\`\`sql
users        → id, name, mobile, password (hashed), created_at
groups       → id, name, code (unique), created_by, created_at
members      → id, group_id, name, user_id
transactions → id, group_id, paid_by_id, amount, reason, created_at
splits       → id, txn_id, member_id, member_name, amount
\`\`\`

## API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| POST | /api/register | Register new user |
| POST | /api/login | Login → returns JWT |
| GET | /api/groups | Get all user's groups |
| POST | /api/groups | Create new group |
| DELETE | /api/groups/\<id\> | Delete group |
| POST | /api/groups/join | Join group by code |
| POST | /api/transactions | Add expense |
| GET | /api/groups/\<id\>/expenses | Group expenses |
| GET | /api/history | Full transaction history |
| GET | /api/groups/\<id\>/settle | Settle up data |

##  How to Run

### Step 1 — Clone the repo
\`\`\`bash
git clone https://github.com/yourusername/billsplitter.git
cd billsplitter
\`\`\`

### Step 2 — Start Backend
\`\`\`bash
cd backend
pip install -r requirements.txt
python app.py
\`\`\`
Backend runs at: **http://localhost:5000**

### Step 3 — Start Frontend
Open `frontend/index.html` with **VS Code Live Server**

App opens at: **http://127.0.0.1:5500**

##  Concepts Learned

### Python
- Flask routes, request handling, jsonify
- JWT authentication (PyJWT)
- Password hashing (werkzeug bcrypt)
- CORS handling (flask-cors)
- Modular file structure
- Error handling with try/except

### SQL (SQLite)
- CREATE TABLE with PRIMARY KEY, FOREIGN KEY
- ON DELETE CASCADE
- INSERT, SELECT, UPDATE, DELETE
- JOIN across multiple tables
- UNIQUE constraints
- Parameterized queries (SQL injection prevention)
- Aggregate functions (SUM, COALESCE)
- Subqueries

### JavaScript
- fetch() with async/await
- JWT token storage in localStorage
- Authorization headers
- React useState, useEffect
- Component-based architecture
- Loading and error states
- Event handling

## Security Features
- Passwords are **bcrypt hashed** — never stored as plain text
- **JWT tokens** expire after 7 days
- **Parameterized SQL queries** — protected against SQL injection
- **CORS** configured for frontend-backend communication

##  Author
Your Name — [@NitinShewale](https://github.com/yourusername)

## 📄 License
MIT License
