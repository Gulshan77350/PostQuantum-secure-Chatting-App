🚀 Features

🔐 User Authentication (JWT / NextAuth)

💬 Real-time chat using WebSockets / Socket.io

🧑‍💻 Secure login & signup

📱 Responsive UI

💾 Persistent chat storage (MongoDB / Firebase)

📦 Tech Stack
Frontend	Backend	Database	Auth	WebSockets
Next.js	Node.js	MongoDB	JWT / NextAuth	Socket.io
📁 Folder Structure
project/
│-- src/
│   ├── app/
│   │   ├── api/
│   │   │   └── auth/
│   │   │       └── login/route.js
│   │   └── (UI pages)
│   ├── components/
│   └── lib/
│-- public/
│-- package.json
│-- README.md

⚙️ Installation
📌 Clone the repository
git clone <repo-url>
cd project

📌 Install dependencies
npm install
# or
yarn install

📌 Setup environment variables

Create a .env.local file in the root directory and add:

MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_secret_key
NEXTAUTH_SECRET=your_secret_key
NEXTAUTH_URL=http://localhost:3000

▶️ Run the Project
npm run dev


App will be available at:
👉 http://localhost:3000

✅ Git Setup Commands

If your project is not initialized yet:

git init


Add and commit files:

git add .
git commit -m "Initial commit"


Add remote and push:

git remote add origin <repo-url>
git branch -M main
git push -u origin main

🛠️ Fix for Login API Error

If your login route throws an error, ensure you return a proper Response in route.js:

import { NextResponse } from "next/server";

export async function POST(req) {
  try {
    const { email, password } = await req.json();

    // Validate user logic

    return NextResponse.json({ success: true, message: "Login successful" });
  } catch (err) {
    return NextResponse.json(
      { success: false, message: err.message },
      { status: 500 }
    );
  }
}
