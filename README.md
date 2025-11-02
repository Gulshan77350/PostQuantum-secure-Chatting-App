````markdown
# 🔐 Secure One-to-One Private Chat — Next.js + Socket.io + MongoDB Atlas

A secure, real-time private chat system built with:

- **Next.js (App Router)**
- **Socket.io**
- **MongoDB Atlas + Mongoose**
- **NextAuth.js (Credentials)**
- **bcryptjs (Password Hashing)**

Supports private one-to-one messaging, persistent chat history, offline delivery, and secure authentication.

---

## 🎯 Objective

Design and implement a **private messaging application** with:

✔ Real-time messages (Socket.io)  
✔ Login system with password hashing  
✔ MongoDB message storage  
✔ Chat history on login  
✔ Offline delivery  
✔ Secure private chat routing  

---

## ✅ Learning Outcomes

- Build full-stack applications using **Next.js App Router**
- Implement **private real-time chat** using Socket.io
- Store and retrieve messages from **MongoDB Atlas**
- Manage sessions and hashed passwords using **NextAuth.js**
- Integrate Socket.io with a custom Node + Next.js server

---

## 🧠 Technologies

| Category | Technology |
|--------|-----------|
Framework | Next.js 16+ (App Router)  
Real-time | Socket.io  
Database | MongoDB Atlas  
ODM | Mongoose  
Authentication | NextAuth.js (Credential Provider)  
Security | bcryptjs (Hashing)  
Server | Node.js custom server.js  

---

## 📦 Requirements

- Node.js **18+**
- npm / yarn
- MongoDB Atlas account

---

## 🚀 Setup and Run

### 1️⃣ Clone Repo
```bash
git clone https://github.com/your-username/your-repo-name.git
cd your-repo-name
````

### 2️⃣ Install Dependencies

```bash
npm install
```

### 3️⃣ Create `.env.local`

```
MONGODB_URI="your-mongodb-uri"
NEXTAUTH_SECRET="your-secret"
NEXTAUTH_URL="http://localhost:3000"
```

Generate secret:

```bash
openssl rand -base64 32
```

### 4️⃣ Allow your IP in MongoDB Atlas

Go to **Network Access → Add Current IP → Save**

### 5️⃣ Start App

```bash
npm run dev
```

Open: **[http://localhost:3000](http://localhost:3000)**

Login in **two browsers** to test private chat.

---

## 📁 Folder Structure

```
CHAT_APK/
├── server.js
├── .env.local
├── next.config.mjs
└── src/
    ├── app/
    │   ├── api/
    │   │   ├── auth/[...nextauth]/route.js
    │   │   ├── messages/route.js
    │   │   └── register/route.js
    │   ├── chat/page.js
    │   ├── layout.js
    │   └── page.js
    ├── lib/
    │   ├── db.cjs
    │   └── socket-handler.cjs
    └── models/
        ├── Message.js
        └── User.js
```

---

## 🔌 API Routes

| Method | Route                         | Description      |
| ------ | ----------------------------- | ---------------- |
| POST   | `/api/register`               | Create user      |
| GET    | `/api/messages?user1=&user2=` | Get chat history |

---

## ⚡ Socket Events

| Event             | Direction       | Purpose                      |
| ----------------- | --------------- | ---------------------------- |
| `send_message`    | Client → Server | Send private message         |
| `receive_message` | Server → Client | Receive message in real-time |

---

## 🛡 Security Features

* Passwords hashed with **bcrypt**
* Secure session tokens (**NextAuth.js**)
* No anonymous users
* Validated private socket sessions

---

## 📸 Screenshots

### 👤 Login / Register

<img src="public/login1.jpeg" width="600">
<img src="public/login2.jpeg" width="600">

### 💬 Chat Interface

<img src="public/chat1.jpeg" width="600">
<img src="public/chat2.jpeg" width="600">

---

## 🧠 Key Learnings

* Combining **Next.js App Router** with custom Node server
* WebSocket integration in full-stack apps
* Handling real-time messages + DB storage
* Managing sessions and authentication securely



## ⭐ Show Support

If this helped you, please ⭐ the repo!

---

```

---

