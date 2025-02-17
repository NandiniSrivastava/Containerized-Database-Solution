```markdown
# MySQL + Docker: Containerized Database Solution

This repository offers a **fully containerized MySQL database** setup using **Docker**, making it easier to deploy, manage, and scale your database environment. Whether you're a developer, a database administrator, or just starting to learn Docker, this guide covers everything you need. 

---

## 📌 Project Overview

This project allows you to **run MySQL inside a Docker container**, with automatic setup via an SQL script. Key features include:

- ✅ **A fully configured MySQL instance** running inside a Docker container 🐬  
- ✅ **Automatic creation of the database and tables** 📦  
- ✅ **Sample data preloaded** for quick testing 📝  
- ✅ **Easy connection to the MySQL database** from any MySQL client 🔗  

---

## 📂 Project Structure

```bash
📂 dockerlab4
│── 📜 Dockerfile            # Instructions to build the MySQL Docker image
│── 🗄️ database.sql           # SQL script for setting up the database & table
│── 📖 README.md             # Documentation for the project
```

---

## 🔧 Prerequisites

Ensure you have the following tools installed:

- **Docker** → [Install Here](https://www.docker.com/get-started) 🐳  
- **MySQL Client** (optional, for connecting to the database externally)

---

## 🚀 Running the MySQL Database

### **1️⃣ Launching MySQL in a Docker Container**

To start the database inside a container, use the following commands:

```bash
docker build -t mysql-db .
docker run --name mysql-container -d -p 3306:3306 mysql-db
```

This will:

- Build a Docker image for MySQL named `mysql-db`.
- Run a MySQL container named `mysql-container`.
- Expose MySQL on **port 3306**.

### **2️⃣ Connecting to the MySQL Database**

To access the database inside the container:

```bash
docker exec -it mysql-container mysql -u root -p
```

Password: `root`

To view the database and tables:

```sql
SHOW DATABASES;
USE student;
SHOW TABLES;
SELECT * FROM students;
```

### **3️⃣ Stopping and Removing the Container**

To stop the container:

```bash
docker stop mysql-container
```

To remove the container:

```bash
docker rm mysql-container
```

---

## 📜 Code Breakdown

### **🔹 `database.sql` – MySQL Database Schema**

- Creates a database called `student`.
- Sets up a `students` table with `StudentID`, `FirstName`, and `Surname`.
- Inserts sample data, such as `John Andersen` and `Emma Smith`.

### **🔹 `Dockerfile` – Containerizing MySQL**

- Uses the **official MySQL image**.
- Sets the **root password** to `root`.
- Copies `database.sql` to **automatically initialize the database** inside the container.

---

## 🎨 Customization & Improvements

Looking to enhance this setup? Consider the following ideas:

- **Expand the database schema** → Add more tables to `database.sql`.
- **Increase security** → Create different user roles with unique passwords.
- **Ensure data persistence** → Mount a Docker volume for persistent database storage.
- **Optimize the Dockerfile** → Use a minimal base image to reduce the image size.

---

## 💡 Troubleshooting

❓ **MySQL container won't start?** Check the logs:

```bash
docker logs mysql-container
```

❓ **Database changes not taking effect?** Rebuild the container:

```bash
docker build --no-cache -t mysql-db .
docker run --name mysql-container -d -p 3306:3306 mysql-db
```

---

