# 🚀 Node.js Express Hello World – DevOps Setup & Deployment

This project demonstrates how to run a simple **Node.js Express** application locally, inside a **Docker container**, and with **Docker Compose**.  
It also includes common issues faced during setup and their solutions.

---

## 📌 Prerequisites
Ensure the following tools are installed on your machine:

- [Git](https://git-scm.com/downloads) → `git --version`
- [Node.js (LTS)](https://nodejs.org/) → `node -v` & `npm -v`
- [Docker Desktop](https://www.docker.com/products/docker-desktop/) → `docker --version`
- Docker Compose → included with Docker Desktop → `docker compose version`

---

## 🔹 1. Clone the Repository
```bash
git clone https://github.com/eMahtab/node-express-hello-world.git
cd node-express-hello-world
```

---

## 🔹 2. Run the App Locally

### Install dependencies

npm install

### Start the app

npm start


### Open in browser
👉 [http://localhost:3000](http://localhost:3000)


## 🔹 3. Dockerize the App

### Create `Dockerfile`

# Use official Node.js LTS image
FROM node:18

# Set working directory
WORKDIR /usr/src/app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install --production

# Copy app source
COPY . .

# Expose port
EXPOSE 3000

# Start the app
CMD ["node", "app.js"]


---

### Build Docker Image

docker build -t node-express-app .


### Run Container

docker run -p 3000:3000 node-express-app


👉 Test in browser: [http://localhost:3000](http://localhost:3000)



## 🔹 4. Run with Docker Compose

### `docker-compose.yml`

services:
  app:
    build: .
    ports:
      - "3000:3000"
```

### `Run`

docker compose up --build


👉 Open in browser: 



## ⚠️ Common Errors & Fixes

### 1. `ERROR: failed to build: EOF`
**Cause:** Empty or invalid `Dockerfile`.  
**Fix:** Ensure `Dockerfile` is not empty and contains valid instructions (see above).


---

## ✅ Final Notes
- Use `npm start` locally for convenience.  
- Use `docker compose up --build` to rebuild and run in containers.  
- If issues persist, run a small test build (e.g., `FROM alpine`) to confirm Docker is working.  

---

👨‍💻 Author: Anuj Tomar  
🎯 Goal: Practice DevOps workflow – Git → Node.js → Docker → Docker Compose.
