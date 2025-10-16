# Project Setup Guide

## 1. Prerequisites
Make sure you have the following installed on your machine:

### For Python projects:
- **Python 3.10+** → [Download here](https://www.python.org/downloads/)
- **pip** (comes preinstalled with Python)
- **virtualenv** (recommended for isolated environments)

### For Node.js projects:
- **Node.js 18+** → [Download here](https://nodejs.org/)
- **npm** (comes with Node.js) or **yarn**

---

## 2. Clone the Repository
Open your terminal and run:
```bash
git clone https://github.com/anamaisuradze01/student-project-repo$0
cd <your-repo-name>
```

---

## 3. Set Up Environment

### 🐍 If using Python:
Create and activate a virtual environment:
```bash
python3 -m venv .venv
source .venv/bin/activate     # On macOS/Linux
# OR
.venv\Scripts\activate        # On Windows
```

Install dependencies:
```bash
pip install -r requirements.txt
```

If you have a `.env.example` file, create your environment file:
```bash
cp .env.example .env
```
Then edit `.env` to add your configuration values (API keys, DB URLs, etc.).

---

### 🌐 If using Node.js:
Install dependencies:
```bash
npm install
# or
yarn install
```

If you have a `.env.example` file:
```bash
cp .env.example .env
```

---

## 4. Run the Project

### For Python:
```bash
python src/main.py
```

### For Node.js:
```bash
npm run start
# or
yarn start
```

---

## 5. Verify Installation
Check that the app runs locally without errors.  
If applicable, visit:
```
http://localhost:3000
```
or whatever port your app uses.

---

## 6. Troubleshooting
If you encounter dependency issues:
- Ensure the correct Python/Node.js version.
- Delete `node_modules` or `.venv` and reinstall dependencies.
- Check environment variables in `.env`.
