Secure One-to-One Private Chat — Next.js + Socket.io + MongoDB Atlas

A fully working 1-to-1 private chat application built with Next.js (App Router), Socket.io for real-time messaging, and MongoDB Atlas for persistence.

Unlike simpler versions, this project implements a full, secure authentication system with user registration, hashed passwords, and session management via NextAuth.js, rather than just basic username entry.

1. Objective

Design and implement a one-to-one private messaging application using Next.js and Socket.io, with messages persisted in MongoDB for chat history and offline delivery.

2. Learning Outcomes

By completing this lab, students will be able to:

Build full-stack apps using Next.js (App Router, API routes, and backend logic).

Implement one-to-one real-time messaging with Socket.io.

Store messages in MongoDB Atlas for history.

Display previous messages on login/open of a chat.

Understand user session management and message routing for private communication.

Additional outcomes from this specific implementation:

Implemented a robust, secure user authentication and session management system using NextAuth.js.

Learned how to integrate Socket.io with a Next.js App Router application by using a custom Node.js server (server.js).

Debugged and solved complex issues related to module formats (ESM vs. CommonJS) and environment variable loading in a custom server environment.

3. Tools & Technologies

Framework: Next.js 16+ (App Router)

Real-time: Socket.io

Database: MongoDB (with Mongoose)

Authentication: NextAuth.js (Credentials Provider)

Password Hashing: bcryptjs

Server: Node.js (Custom server.js)

Environment Variables: dotenv

4. Prerequisites

Node.js 18+

npm (or yarn)

A MongoDB Atlas account and a connection URI

5. Setup & Run Locally

Follow these steps exactly to run the project.

Step 1: Clone the Repository

# Clone the repository
git clone [https://github.com/your-username/your-repo-name.git](https://github.com/your-username/your-repo-name.git)
cd your-repo-name


Step 2: Install Dependencies

# Install all required packages
npm install


Step 3: Set Up Environment Variables

Create a file named .env.local in the root of the project. This file holds all the secret keys.

# .env.local

# 1. MongoDB Connection String
# Get this from your MongoDB Atlas dashboard
MONGODB_URI="mongodb+srv://<your_username>:<your_password>@<your_cluster_url>/<your_database_name>?retryWrites=true&w=majority"

# 2. NextAuth.js Keys
# Generate a random secret (e.g., openssl rand -base64 32)
NEXTAUTH_SECRET="your-super-strong-secret-key"
NEXTAUTH_URL="http://localhost:3000"


Step 4: Configure MongoDB Atlas IP Access

You must authorize your computer to connect to the database.

Log in to your MongoDB Atlas dashboard.

Go to the "Network Access" tab.

Click "Add IP Address".

Click "Allow Current IP Address" and confirm. (Wait for it to become "Active").

Step 5: Run the Application

This project uses a custom server, so you must use node server.js to run it.

# Run the development server
npm run dev


Your application is now running at http://localhost:3000. Open two different browser windows to log in with two different users and test the chat.

6. Architecture & Project Structure

This project uses a custom Node.js server (server.js) to run both the Next.js application and the Socket.io server within the same process. This is the modern, robust way to integrate Socket.io with the Next.js App Router.

CHAT_APK/
│
├── 📄 server.js             # **Custom Node.js server (starts Next.js & Socket.io)**
├── 📄 .env.local            # Secret keys (MongoDB, NextAuth)
├── 📄 next.config.mjs       # Next.js configuration
├── 📄 package.json
│
└── 📁 src/
    ├── 📁 app/
    │   │
    │   ├── 📁 api/
    │   │   ├── 📁 auth/[...nextauth]/ # NextAuth.js routes
    │   │   │   └── route.js
    │   │   ├── 📁 messages/         # API to fetch chat history
    │   │   │   └── route.js
    │   │   └── 📁 register/         # API to create new users
    │   │       └── route.js
    │   │
    │   ├── 📁 chat/                 # The main chat page (Client Component)
    │   │   └── page.js
    │   │
    │   ├── 📄 layout.js             # Root layout (with AuthProvider)
    │   └── 📄 page.js               # Login/Registration page (Client Component)
    │
    ├── 📁 lib/
    │   ├── 📄 db.cjs                # MongoDB connection logic (CommonJS)
    │   └── 📄 socket-handler.cjs    # **All Socket.io server logic (CommonJS)**
    │
    └── 📁 models/                   # Mongoose Schemas (CommonJS)
        ├── 📄 Message.js
        └── 📄 User.js


7. API & Socket Event Details

REST API (Next.js)

POST /api/register: Creates a new user in the users collection.

POST /api/auth/callback/credentials: (Handled by NextAuth.js) Authenticates a user via username/password and returns a session.

GET /api/messages?user1=...&user2=...: Securely fetches the chat history between the two specified users.

Socket.io Events (socket-handler.cjs)

On Connection:

Client provides auth: { username }.

Server middleware validates the username and maps username -> socket.id.

Client Emits:

send_message({ receiver, text }): Client sends a new message. The sender is securely identified on the server from the socket.

Server Emits:

receive_message({ sender, text }): Server pushes the new message in real-time to the intended receiver if they are online.

8. Screenshots

(Replace these with your own screenshots)

Login & Registration Page

Main Chat Interface

<img width="600" alt="Login Page Screenshot" src="/home/aditya/Documents/chatapk_v2/chat_apk/public/login1.jpeg">

<img width="600" alt="Chat Interface Screenshot" src="/home/aditya/Documents/chatapk_v2/chat_apk/public/login2.jpeg">

<img width="600" alt="Chat Interface Screenshot" src="h/home/aditya/Documents/chatapk_v2/chat_apk/public/chat1.jpeg">

<img width="600" alt="Chat Interface Screenshot" src="h/home/aditya/Documents/chatapk_v2/chat_apk/public/login2.jpeg">