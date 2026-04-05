# 🐳 Docker Basics (Notes)

## 🧠 Flow
Code → Dockerfile → Image → Container → App Running


## 🟢 Dockerfile (Recipe)
FROM node:20-alpine

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

EXPOSE 5000

CMD ["node", "server.js"]

### Meaning (simple)
1. Use Node environment
2. Work inside /app
3. Copy package files
4. Install dependencies
5. Copy code
6. App runs on port 5000
7. Start server

## 🟡 Build Image
docker build -t dummy-backend .

### Meaning
Dockerfile → executed → creates IMAGE (packaged app)

## 🔵 Run Container
docker run -p 5000:5000 --name dummy --env-file .env dummy

### Meaning
Image → becomes Container → app starts running

## 🔥 Port Mapping
-p host:container

Example:
docker run -p 5000:5000 dummy-backend
localhost:5000 → container:5000

## 🧠 Key Concepts
Dockerfile → recipe  
Image → packaged app  
Container → running app  

----------------------------------------------------------------------------------------------------

## 🐳 Docker Compose (Multi-Container Setup)

### 🧠 Why Docker Compose?

Till now, we were running containers manually:
backend → separate command  
frontend → separate command  

👉 Problems:

* too many commands
* containers don’t know each other
* hard to manage system

### ✅ What Compose solves
Run full system (frontend + backend) together  
Shared network (containers talk via names)  
Single command to manage everything  

### 🧠 Key Idea
docker run → one container  
docker-compose → entire system

## 🚀 Commands

### ▶️ Start everything (build + run)
docker-compose up --build

👉 Builds images + starts containers
👉 Runs in foreground (shows logs)

### ▶️ Start in background (detach mode)
docker-compose up --build -d

👉 Runs in background
👉 terminal stays free

### 🛑 Stop everything
docker-compose down
👉 Stops and removes containers

### 📜 View logs
docker-compose logs

👉 logs of all services

### 📜 Logs of specific service
docker-compose logs backend
docker-compose logs frontend

