
---

# 🚀 Deploying a MERN Stack Project to Vercel

This guide explains how to deploy a **MERN (MongoDB, Express, React, Node.js)** project to **Vercel** — where your backend (server) and frontend (client) are in separate folders.

---

## 📁 Project Structure

You should have a main folder containing two subfolders:

```
project/
│
├── server/
│
├── client/
│
└── .gitignore
```

---

## 📝 Step 1: Create a `.gitignore` File

Inside your root project folder, create a `.gitignore` file and add the following lines:

```bash
node_modules
.env
```

This ensures that unnecessary and sensitive files are not pushed to GitHub.

---

## ⚙️ Step 2: Setup the Server Folder for Deployment

Navigate to your **server** directory:

```bash
cd server
```

Create a new file named **`vercel.json`** and add the following configuration:

```json
{
  // vercel configuration for express backend
  "version": 2,
  "builds": [
    {
      "src": "./index.js",
      "use": "@vercel/node"
    }
  ],
  "routes": [
    {
      "src": "/(.*)",
      "dest": "/index.js"
    }
  ]
}
```

> ⚠️ Make sure your `index.js` (or app entry file) is correctly named and exports your Express app.

---

## ⚙️ Step 3: Setup the Client Folder for Deployment

Go to your **client** directory:

```bash
cd ../client
```

If your React app is created with **create-react-app**, you can also create a `vercel.json` file here (optional but recommended):

```json
{
  "version": 2,
  "builds": [
    {
      "src": "package.json",
      "use": "@vercel/static-build"
    }
  ],
  "routes": [
    {
      "src": "/(.*)",
      "dest": "/index.html"
    }
  ]
}
```

Make sure your **build script** is correctly set in `package.json`:

```json
"scripts": {
  "start": "react-scripts start",
  "build": "react-scripts build"
}
```

---

## 💾 Step 4: Push the Project to GitHub

1. Initialize Git (if not already):

   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   ```

2. Add your GitHub repository as a remote and push:

   ```bash
   git remote add origin https://github.com/yourusername/your-repo.git
   git push -u origin main
   ```

---

## 🌐 Step 5: Deploy Backend to Vercel

1. Go to **[vercel.com](https://vercel.com)**
2. Log in or Sign up using your GitHub account
3. From the **Dashboard**, click **“Add New → Project”**
4. Import your GitHub repository
5. Configure the following:

   - **Project name:** your backend name
   - **Root directory:** `/server`
   - **Environment Variables:** add the same variables used in your `.env` file

6. Click **Deploy**

---

## 🧩 Step 6: Fixing Common Errors

After deployment, you might see an error on your backend URL.
This can happen if:

- Environment variables are missing or incorrect
- Local and production paths differ

✅ **Solution:**

- Recheck your environment variables in Vercel (`Settings → Environment Variables`)
- Make sure your code checks for production mode properly:

```js
const PORT = process.env.PORT || 5000;
const MONGO_URI = process.env.MONGO_URI;

app.listen(PORT, () => console.log(`Server running on port ${PORT}`));
```

- After updating, **Redeploy** your project in Vercel.

---

## 💻 Step 7: Deploy the Client to Vercel

Repeat similar steps for the **client folder**:

1. Create a new Vercel project
2. Select the **same GitHub repository**
3. Choose the **root directory:** `/client`
4. Set required **Environment Variables** (like API URLs)
5. Click **Deploy**

---

## ✅ Step 8: Connect Client and Server

After both are deployed:

- Copy the **backend URL** from Vercel (e.g., `https://your-backend.vercel.app`)
- Update your frontend `.env` or API base URL with this backend link
- Redeploy the **client** app

---

## 🎉 Done!

Now your **MERN app** is successfully deployed on **Vercel** — both backend and frontend hosted separately but connected through their respective URLs.

---
