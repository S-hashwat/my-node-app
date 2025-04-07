# 🚀 My Node.js App with CI/CD Pipeline

This project is a simple **Node.js** web application built from scratch and integrated with a **CI/CD pipeline** using **GitHub Actions** and **Docker**. The pipeline automates testing, Docker image creation, and more on every push to the `main` branch.

---

## ✅ What We Did

### 1. Set up the Project Locally
- Installed Node.js and npm on Windows 10.
- Created a new folder named `my-node-app`.
- Initialized the project:
  ```bash
  npm init -y


Installed Express:
npm install express

Created a basic app.js file:

javascript
Copy
Edit
const express = require('express');
const app = express();
const port = 3000;

app.get('/', (req, res) => {
  res.send('Hello from Shashwat\'s Node app!');
});

app.listen(port, () => {
  console.log(`App running at http://localhost:${port}`);
});
2. Created a Dockerfile
Dockerfile
Copy
Edit
# Use official Node.js base image
FROM node:18

# Set working directory
WORKDIR /app

# Copy package.json and install dependencies
COPY package*.json ./
RUN npm install

# Copy rest of the app
COPY . .

# Expose port
EXPOSE 3000

# Run the app
CMD ["node", "app.js"]
3. Ran Docker Locally
Make sure Docker Desktop is installed and running.

bash
Copy
Edit
docker build -t shashwat-node-app .
docker run -p 3000:3000 shashwat-node-app
4. GitHub Repo Setup
Created a GitHub repo (e.g., my-node-app).

Initialized git:

bash
Copy
Edit
git init
git remote add origin https://github.com/S-hashwat/my-node-app.git
git add .
git commit -m "Initial commit"
git push -u origin main
5. Created GitHub Actions CI/CD Workflow
File: .github/workflows/main.yml

yaml
Copy
Edit
name: Node.js CI/CD

on:
  push:
    branches: [ "main" ]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Set up Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '18'

      - name: Install dependencies
        run: npm install

      - name: Run tests (if any)
        run: echo "No tests yet"

      - name: Build Docker image
        run: docker build -t shashwat-node-app .
🔐 If you plan to push Docker images to DockerHub, create GitHub Secrets:

DOCKER_USERNAME

DOCKER_PASSWORD

And add Docker login + push steps in the workflow.

🧪 How to Run Locally
bash
Copy
Edit
git clone https://github.com/S-hashwat/my-node-app.git
cd my-node-app
npm install
node app.js
Then open http://localhost:3000

📁 Folder Structure
perl
Copy
Edit
my-node-app/
├── .github/
│   └── workflows/
│       └── main.yml         # GitHub Actions pipeline
├── Dockerfile               # Docker configuration
├── app.js                   # Main Express app
├── package.json             # NPM metadata
└── README.md                # This file
💡 Technologies Used
Node.js

Express.js

Docker

GitHub Actions (CI/CD)

VS Code
