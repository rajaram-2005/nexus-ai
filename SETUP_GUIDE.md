# How to Download & Run This Project

> A step-by-step guide for anyone cloning this repository.

---

## Prerequisites

Before you begin, make sure you have installed:

- **Node.js** (version 18 or higher) — [Download here](https://nodejs.org/)
- **npm** (comes with Node.js)
- **Git** — [Download here](https://git-scm.com/)

To verify your installation, open your terminal and run:

```bash
node -v
npm -v
git -v
```

If you see version numbers, you are ready to proceed.

---

## Step 1: Clone the Repository

Open your terminal (Command Prompt on Windows, Terminal on Mac/Linux) and run:

```bash
git clone https://github.com/YOUR_USERNAME/nexus-ai.git
```

Replace `YOUR_USERNAME` with the actual GitHub username of the repository owner.

After cloning, navigate into the project folder:

```bash
cd nexus-ai
```

---

## Step 2: Install Dependencies

You need to install packages for both the server and the client.

### Install server dependencies:

```bash
npm install
```

### Install client dependencies:

```bash
cd client
npm install
cd ..
```

---

## Step 3: Set Up Environment Variables

This project requires a `.env` file for configuration.

1. Check if a `.env` file exists in the root folder.
2. If it does not exist, create one by copying the example file:

**On Windows:**
```bash
copy .env.example .env
```

**On Mac or Linux:**
```bash
cp .env.example .env
```

The default contents should be:

```env
DATABASE_URL="file:./prisma/dev.db"
JWT_SECRET="nexus_ai_super_secret_change_me_in_production"
```

> **Security tip:** Change the `JWT_SECRET` value to a long, random string before deploying to production.

---

## Step 4: Set Up the Database

Run the following command to create the SQLite database and apply the schema:

```bash
npm run db:push
```

Then seed the database with a demo account:

```bash
npm run db:seed
```

You should see output like:

```
Seed complete.
Login with: demo@nexus.ai / demo1234
```

---

## Step 5: Start the Application

Run both the backend server and frontend client with one command:

```bash
npm run dev
```

This will start:

- **Backend API** at http://localhost:3001
- **Frontend** at http://localhost:3000

---

## Step 6: Open in Browser

1. Open your web browser
2. Go to http://localhost:3000
3. Log in using the demo credentials:

| Field | Value |
|-------|-------|
| Email | `demo@nexus.ai` |
| Password | `demo1234` |

---

## Step 7: Add Your Own AI Provider (Required for Chat)

Before you can start chatting, you need to add an API provider:

1. Click the **Settings** icon (gear icon) in the top-right corner
2. Go to the **API Providers** tab
3. Click **Add Provider**
4. Fill in the details:
   - **Name:** Any name you want (e.g., `My OpenRouter`)
   - **Type:** `openai` (for OpenAI-compatible APIs)
   - **Base URL:** Your provider's API endpoint (e.g., `https://openrouter.ai/api/v1`)
   - **API Key:** Your actual API key from the provider
   - **Model ID:** The model you want to use (e.g., `gpt-4o`, `openai/gpt-3.5-turbo`)
5. Click **Add Provider**
6. Now click **New Chat** in the sidebar and start chatting

---

## Troubleshooting

### Error: `vite is not recognized`

This means client dependencies are not installed. Run:

```bash
cd client
npm install
cd ..
npm run dev
```

### Error: `Database file not found`

Run the database setup again:

```bash
npm run db:push
npm run db:seed
```

### Error: `Port already in use`

If ports 3000 or 3001 are already in use by another application:

1. Close any other applications using those ports
2. Or modify the ports in:
   - `server/index.js` (change `PORT`)
   - `client/vite.config.js` (change `port`)

---

## Alternative: One-Command Setup

If you prefer, you can run the automated setup script:

```bash
node scripts/setup.js
npm run dev
```

This will install all dependencies, create the database, and seed it automatically.

---

## Need Help?

If you encounter any issues:

1. Make sure you are using **Node.js 18 or higher**
2. Delete `node_modules` folders and reinstall:
   ```bash
   rm -rf node_modules client/node_modules
   npm install
   cd client && npm install && cd ..
   ```
3. Check that your `.env` file exists and is correctly formatted

---

**Happy coding!**
