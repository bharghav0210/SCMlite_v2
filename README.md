# SCMlite: Supply Chain Management System

SCMlite_v2 is a secure and robust web application for managing supply chain shipments, built with FastAPI and MongoDB. It features a complete user authentication system, role-based access control (admin/user), and full CRUD (Create, Read, Update, Delete) operations for shipments and user management.

The application is containerized using Docker and designed for deployment on cloud platforms like AWS.

---

## Key Features

* **User Authentication:** Secure user registration (`/signup`) and login (`/login`) system with password hashing (`bcrypt`) and session handling.
* **Role-Based Access Control (RBAC):**
    * **User Role:** Can view their dashboard, create shipments, view all shipments, and manage their own account.
    * **Admin Role:** Has full access, including a separate admin dashboard, all user privileges, and an admin-only user management panel.
* **User Management (Admin):**
    * View all registered users.
    * Edit user details (name, email, role).
    * Delete users from the system.
    * Assign/revoke admin privileges.
* **Shipment Management:**
    * **Users:** Can create new shipments with detailed information (PO, route, device, etc.).
    * **Admins:** Can edit, update status, and delete any existing shipment.
    * **All Users:** Can view a list of all shipments and their current status.
* **Device Data:** A dedicated page (`/device-data`) to display real-time sensor data from the MongoDB collection.
* **Security:**
    * **Google reCAPTCHA:** Protects the login form from bots.
    * **Session Handling:** Uses `starlette.middleware.sessions` to manage user sessions.
    * **Password Hashing:** Uses `passlib` to securely hash and verify user passwords.
* **Logging:** Comprehensive logging (to `app.log` and console) records endpoint access, user actions, and potential errors.

---

##  Technology Stack

* **Backend:** [FastAPI](https://fastapi.tiangolo.com/) (Python 3)
* **Database:** [MongoDB](https://www.mongodb.com/) (connected via MongoDB Atlas)
* **Templating:** [Jinja2](https://jinja.palletsprojects.com/)
* **Authentication:** `passlib[bcrypt]`, Session Middleware
* **Security:** Google reCAPTCHA
* **Containerization:** [Docker](https://www.docker.com/)
* **Deployment:** [AWS](https://aws.amazon.com/) (or any cloud provider)

---

##  Setup and Installation

You can run the application locally using either Docker (recommended) or a Python virtual environment.

### 1. Prerequisites

* Python 3.8+
* Docker (for Docker setup)
* A MongoDB Atlas account (or a local MongoDB instance)
* Google reCAPTCHA v2 (Site Key and Secret Key)

### 2. Configuration

Create a file named `.env` in the root of the project and add the following environment variables.

```.env
# FastAPI & Sessions
SECRET_KEY="your_very_strong_secret_key_here"
ALGORITHM="HS256"
ACCESS_TOKEN_EXPIRE_MINUTES=30

# MongoDB
MONGO_URI="mongodb+srv://<username>:<password>@<cluster-url.mongodb.net>/..."

# Google reCAPTCHA
RECAPTCHA_SITE_KEY="your_recaptcha_site_key"
RECAPTCHA_SECRET_KEY="your_recaptcha_secret_key"


