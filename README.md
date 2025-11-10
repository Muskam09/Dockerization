# Dockerized Todolist (Django + MySQL)

This project demonstrates how to use `docker-compose` to build and run a multi-container Django application with a MySQL database.

## 🎯 Project Goal

The primary goal was to correctly orchestrate the services, specifically:

* **Persistent Data:** A Docker volume (`db-data`) is used for the MySQL service to ensure that all todo items are saved even after containers are restarted.
* **Startup & Migrations:** The application's `ENTRYPOINT` is configured to run Django database migrations (`manage.py migrate`) *before* starting the web server. This prevents race conditions where the app starts before the database schema is ready.

## 🛠️ Stack

* **Application (`pythonapp`):** The Python/Django Todolist app.
* **Database (`mysql`):** The MySQL database service.

## 🚀 How to Run

### Prerequisites

* Docker
* Docker Compose

### 1. Clone the Repository

```
git clone https://github.com/Muskam09/Dockerization.git
cd Dockerization
```

### 2. Build and Run Services
This single command will build the custom images (if they don't exist) and start both the application and database containers.

``` docker-compose up --build ```

### 3. Access the Application
Once the containers are running, you can access the services:

Todolist Application: http://localhost:8089

Database (External Tool):  http://localhost:3307

⏹️ How to Stop
1. Stop and Remove Containers
To stop and remove the containers and network:

``` docker-compose down ```

2. Stop and Remove Volume (Warning!)
If you also want to delete all data (including your todo items in the database), run:

``` docker-compose down -v ```
