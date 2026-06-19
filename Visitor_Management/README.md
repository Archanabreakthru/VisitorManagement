# Breakthru.ai Visitor Management System (VMS)

A premium, interactive, and modern web application to streamline visitor check-ins and check-outs, built with HTML, CSS, JavaScript, Node.js, Express, and PostgreSQL.

---

## 🚀 Key Features

* **Multi-Mode Reception Access**: Support for both **RFID Card** badge-issuing and **QR-code** visual badges.
* **OTP Verification**: Multi-factor verification (Email) during visitor registration.
* **Host Notification & Approvals**: Real-time host email approvals and Telegram alerts.
* **Smart Checkout Lookup**: Flexible search validation allowing check-out by scanning QR, tapping RFID card, entering phone numbers (with country code prefix handling), or entering emails.
* **Autofill Blocking**: Hard blocks on browser autofill suggestions on reception input fields for cleaner kiosks.
* **Auto-Close Lifecycle**: Scheduled checkout scripts to clean up outstanding visitors daily at 18:30.

---

## 🛠️ Technology & Languages

* **Frontend**: HTML5, Vanilla CSS3, Vanilla JavaScript (ES6+).
* **Backend**: Node.js, Express.js.
* **Database**: PostgreSQL (Structured queries).
* **Alert Integrations**: Telegram Bot API, Nodemailer (SMTP/Gmail).

---

## 📂 Project Structure

```text
Visitor_Management/
├── backend/
│   ├── config/
│   │   └── db.js            # DB client connection pool
│   ├── routes/
│   │   ├── appointments.js  # Pre-scheduled visit lookups
│   │   ├── hosts.js         # Hosts directory management
│   │   ├── rfid.js          # Card slot trackers
│   │   ├── visits.js        # Core visit operations (check-in/checkout/search)
│   │   └── otp.js           # Verification endpoint
│   ├── services/
│   │   ├── emailService.js  # NodeMailer handler
│   │   └── telegramService.js # Bot notification routines
│   ├── server.js            # Express server configuration
│   └── package.json         # Backend manifest
└── frontend/
    ├── vms_fixed.html       # Single-page kiosk UI
    ├── api-bridge.js        # Fetch router mapping to backend API
    └── BT_Logo_2_w.png      # Application branding assets
```

---

## 💻 Local Setup & Development

### 1. Requirements
* [Node.js](https://nodejs.org/) (v16+)
* [PostgreSQL](https://www.postgresql.org/) (v13+)

### 2. Environment Configuration
Create a `.env` file in `Visitor_Management/backend/` with the following variables:
```env
# Server Port
PORT=3001

# PostgreSQL Database Configuration
PG_HOST=localhost
PG_PORT=5432
PG_DATABASE=vms_db
PG_USER=postgres
PG_PASSWORD=your_secure_password

# Email Alerts Configuration
MAIL_HOST=smtp.gmail.com
MAIL_PORT=587
MAIL_USER=your_email@gmail.com
MAIL_PASS=your_app_password
MAIL_FROM=no-reply@breakthru.ai

# Telegram Configuration
TELEGRAM_BOT_TOKEN=your_bot_token
TELEGRAM_CHAT_ID=your_chat_id

# Kiosk Verification Link
BASE_URL=http://localhost:3001
```

### 3. Install Dependencies & Start Server
Navigate to the backend directory and launch:
```bash
cd Visitor_Management/backend
npm install
npm run dev
```
Open **[http://localhost:3001](http://localhost:3001)** in your browser.

---

## ☁️ Deploying to Render (Step-by-Step)

### Step 1: Create a PostgreSQL Database
1. Go to [Render Dashboard](https://dashboard.render.com/) -> **New** -> **PostgreSQL**.
2. Set Name to `vms-db` and Database to `vms_db`.
3. Select the **Free** tier and click **Create Database**.
4. Copy the **Internal Database URL** (or Host, Password details).

### Step 2: Create Web Service
1. Click **New** -> **Web Service**.
2. Connect your Git repository.
3. Configure:
   * **Root Directory**: `Visitor_Management/backend`
   * **Build Command**: `npm install`
   * **Start Command**: `node server.js`
4. Click **Advanced** and add your environment variables matching your `.env` configuration (use Render DB credentials for host, user, password, and port).
5. Click **Create Web Service**.
