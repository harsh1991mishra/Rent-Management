# Rent-Management
# 🏢 Shyam Sadan PG — Rent & Property Management System

A full-stack, zero-cost, cloud-powered PG & Hostel Management Web Application built for **Shyam Sadan PG** (Sector 35, Noida). Hosted on **GitHub Pages** and powered by **Google Sheets, Google Apps Script, Google Sign-In, UPI Deep Links, and WhatsApp Cloud API**.

🌐 **Live Portal:** `https://harsh1991mishra.github.io/Rent-Management/`  
💬 **Direct Owner Support:** [Chat with Shivam Sharma on WhatsApp](https://wa.me/919953761010?text=Namaste%20Shivam%20ji,%20I%20would%20like%20to%20inquire%20about%20Shyam%20Sadan%20PG.)

---

## 📍 Property Details
* **PG Name:** Shyam Sadan PG
* **Owner:** Shivam Sharma
* **Contact / WhatsApp:** +91 99537 61010
* **Address:** Sector 35, Noida, Uttar Pradesh – 201301
* **Capacity:** 4 Buildings (~40 Rooms per building | ~160 Rooms total)
* **Monthly Rent Due Date:** 10th of every month

---

## ✨ Key Features

### 1. Admin Dashboard (Google Sign-In Protected)
* **Multi-Building Switcher:** Seamlessly manage **Building 1, Building 2, Building 3, and Building 4**.
* **Visual Room & Bed Occupancy Grid:** Color-coded status cards (`Green` = Vacant, `Red` = Occupied, `Yellow` = Notice Period) across Single, Double, and Triple sharing rooms.
* **Digital Tenant Onboarding & KYC:** Captures tenant contact details, emergency contacts, security deposit, joining date, and uploads ID proofs directly to **Google Drive**.
* **Automated Monthly Billing:** Generates monthly rent entries on the **1st of every month**, with support for sub-meter electricity units, mess charges, and automated late fees after the **10th**.
* **Expense & Net Profit Tracker:** Logs building-wise electricity bills, maintenance, and staff salaries to calculate real-time net monthly profit.

### 2. Tenant Self-Service Portal (Mobile-Friendly)
* **Instant Access:** Tenants log in using their registered mobile number to view current dues and payment history.
* **Zero-Fee Direct UPI Payments:**
  * One-tap **UPI Deep Link** (`upi://pay`) pre-filled with exact rent amount and room number for GPay, PhonePe, and Paytm.
  * Dynamic **QR Code** (`qrcode.js`) for instant desktop-to-mobile scanning.
  * **UTR Verification:** Tenants submit their 12-digit UPI UTR reference number for one-click owner approval.
* **Instant PDF Invoices:** Generates branded **Shyam Sadan Rent Receipts** (`jsPDF`) upon payment confirmation.
* **Complaint & Maintenance Box:** Raise room-tagged tickets (Wi-Fi, Plumbing, Electrical, AC) tracked directly by management.

### 3. Automated WhatsApp Reminders (10th Due Date Cycle)
Powered by **Google Apps Script Time-Driven Triggers** & **Meta WhatsApp Cloud API**:
* **7th of Month:** Friendly advance rent reminder with direct UPI payment link.
* **10th of Month:** Due-date reminder.
* **12th & 15th of Month:** Overdue alert with late fee notice for unpaid accounts.
* **Floating WhatsApp Chatbox:** Instant 1-click WhatsApp support chat with owner **Shivam Sharma** (`+91 99537 61010`).

---

## 🛠️ Tech Stack
* **Frontend:** HTML5, CSS3, Vanilla JavaScript (ES6+), `qrcode.js`, `jsPDF`
* **Authentication:** Google Identity Services (OAuth 2.0)
* **Backend & Database:** Google Apps Script + Google Sheets
* **Document Storage:** Google Drive API (via Apps Script)
* **Messaging:** Meta WhatsApp Cloud API & `wa.me` Deep Links
* **Hosting:** GitHub Pages

---

## 🚀 Setup & Deployment Guide

### Step 1: Google Sheet & Apps Script Setup
1. Create a new Google Sheet named `Shyam_Sadan_PG_DB` with 5 tabs:
   * `Rooms` | `Tenants` | `RentLedger` | `Expenses` | `Complaints`
2. Open **Extensions > Apps Script**, paste the code from `backend/Code.gs`, and configure:
   * `OWNER_EMAIL`: Admin Gmail address for dashboard access.
   * `DRIVE_FOLDER_ID`: Google Drive folder ID for tenant KYC documents.
   * `WHATSAPP_TOKEN` & `PHONE_NUMBER_ID`: From Meta Developer Portal.
3. Click **Deploy > New Deployment > Web App** (Execute as: *Me*, Who has access: *Anyone*) and copy the Web App URL.
4. Set a **Time-Driven Trigger** in Apps Script to run `dailyScheduler()` every day between **10:00 AM – 11:00 AM**.

### Step 2: Configure Google Sign-In
1. Go to [Google Cloud Console](https://console.cloud.google.com/) and create an OAuth 2.0 Client ID (Web Application).
2. Add `https://harsh1991mishra.github.io` to **Authorized JavaScript Origins**.
3. Copy your Client ID into `js/config.js`.

### Step 3: Deploy on GitHub Pages
1. Clone this repository:
   ```bash
   git clone [https://github.com/harsh1991mishra/Rent-Management.git](https://github.com/harsh1991mishra/Rent-Management.git)
