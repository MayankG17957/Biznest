# BizNest

> **AI-Powered Shop Intelligence & Management System**

BizNest is a modern shop management platform designed to help businesses manage their day-to-day operations from a single system. It combines **inventory, products, sales, purchases, customers, payments, staff management, and AI-powered business intelligence** to turn operational data into useful insights.

---

## 🚀 Key Features

### 📦 Product & Inventory Management
- Add, update, view, and delete products
- Product categorization and stock tracking
- Stock-in and stock-out transactions
- Low-stock monitoring
- Product image support
- Inventory movement tracking

### 🛒 Sales Management
- Create and manage sales
- Customer-linked sales
- Track sold products and quantities
- Calculate sales revenue
- Monitor sales history

### 📥 Purchase Management
- Record purchases
- Track purchase costs
- Maintain supplier/purchase information
- Update inventory through stock transactions

### 👥 Customer Management
- Add and manage customers
- Maintain customer purchase history
- Track customer-related sales
- Support customer payment/hisaab tracking

### 💰 Payments & Hisaab
- Record customer payments
- Track pending amounts
- Monitor payment history
- Calculate outstanding customer balances

### 👨‍💼 Staff Management
- Staff management
- Role-based access
- Attendance management
- Salary management

### 📊 Dashboard & Analytics
The dashboard provides an overview of important business metrics, including:
- Total products
- Total sales
- Total purchases
- Total payments
- Low-stock products
- Total sales revenue
- Purchase cost
- Basic profit
- Pending payment amount

### 🤖 AI Shop Intelligence
BizNest includes a dedicated AI service for business intelligence and decision support.

AI capabilities include:
- Sales analysis
- Demand prediction
- Restock recommendations
- Business insights
- Revenue forecasting
- Anomaly detection
- AI assistant
- Product recommendations
- Model training using business data

The demand-prediction system uses a **Random Forest machine-learning model** trained with sales data from the PostgreSQL database.

---

## 🏗️ System Architecture

BizNest is divided into three major applications:

```text
                    ┌─────────────────────┐
                    │   React Frontend    │
                    │ Vite + Tailwind CSS │
                    │      Port 5173      │
                    └──────────┬──────────┘
                               │ REST API
                               ▼
                    ┌─────────────────────┐
                    │   Spring Boot API   │
                    │       Port 8080     │
                    │ JPA + REST + Auth   │
                    └───────┬─────┬───────┘
                            │     │
                 PostgreSQL │     │ AI API
                            ▼     ▼
                    ┌──────────┐ ┌──────────────┐
                    │PostgreSQL│ │ FastAPI AI   │
                    │  biznest │ │ Service      │
                    │  :5432   │ │    :8000     │
                    └──────────┘ └──────────────┘
```

### Project Structure

```text
BizNest/
│
├── biznest-backend/
│   └── Spring Boot REST API
│
├── biznest-frontend/
│   └── React + Vite + Tailwind CSS application
│
└── biznest-ai/
    └── Python FastAPI AI/ML service
```

---

## 🛠️ Tech Stack

### Frontend
- React
- Vite
- Tailwind CSS
- JavaScript
- REST API integration

### Backend
- Java
- Spring Boot
- Spring Data JPA
- Spring Security
- JWT Authentication
- Maven
- REST APIs

### Database
- PostgreSQL
- Database name: `biznest`

### AI / Machine Learning
- Python
- FastAPI
- Machine Learning
- Random Forest
- PostgreSQL-based training data

### Development & Testing
- Git & GitHub
- Postman
- IntelliJ IDEA / VS Code
- PostgreSQL tools

---

## 🔐 Authentication & Authorization

BizNest uses authentication and role-based access control.

Supported roles include:

- **ADMIN** — manages the complete system and business operations
- **STAFF** — accesses permitted operational features

Authentication is implemented using **Spring Security and JWT**.

Typical authentication flow:

```text
User Login
    ↓
Spring Boot Authentication
    ↓
JWT Token
    ↓
Frontend stores/uses token
    ↓
Authenticated API Requests
    ↓
Role-based authorization
```

---

## 📊 Core Modules

```text
Dashboard
│
├── Products
│   ├── Product CRUD
│   └── Product Images
│
├── Inventory
│   ├── Stock In
│   ├── Stock Out
│   └── Low Stock
│
├── Sales
│   ├── Sales
│   └── Customer Sales
│
├── Purchases
│
├── Customers
│
├── Payments / Hisaab
│
├── Staff
│   ├── Attendance
│   └── Salary
│
└── AI Intelligence
    ├── Sales Analysis
    ├── Demand Prediction
    ├── Restock
    ├── Revenue Forecast
    ├── Anomaly Detection
    ├── Recommendations
    └── AI Assistant
```

---

## ⚙️ Local Development Setup

### 1. Clone the repository

```bash
git clone <your-repository-url>
cd BizNest
```

---

### 2. Configure PostgreSQL

Create a PostgreSQL database:

```sql
CREATE DATABASE biznest;
```

Configure the database credentials in the Spring Boot application's configuration.

Example:

```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/biznest
spring.datasource.username=YOUR_USERNAME
spring.datasource.password=YOUR_PASSWORD
```

> Do not commit real database passwords, JWT secrets, API keys, or other credentials to GitHub.

---

### 3. Run the Spring Boot Backend

Move into the backend directory:

```bash
cd biznest-backend
```

Run using Maven:

```bash
./mvnw spring-boot:run
```

On Windows:

```bash
mvnw.cmd spring-boot:run
```

Backend:

```text
http://localhost:8080
```

---

### 4. Run the AI Service

Move into the AI service:

```bash
cd biznest-ai
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Start FastAPI:

```bash
uvicorn main:app --reload --port 8000
```

AI service:

```text
http://localhost:8000
```

FastAPI documentation is normally available at:

```text
http://localhost:8000/docs
```

---

### 5. Run the Frontend

Move into the frontend:

```bash
cd biznest-frontend
```

Install dependencies:

```bash
npm install
```

Start the development server:

```bash
npm run dev
```

Frontend:

```text
http://localhost:5173
```

---

## 🔄 Application Flow

A typical business operation follows this flow:

```text
User
 │
 ▼
React Frontend
 │
 ▼
Spring Boot REST API
 │
 ├──────────────► PostgreSQL
 │
 └──────────────► FastAPI AI Service
                         │
                         ▼
                    ML Predictions
                         │
                         ▼
                  Business Insights
                         │
                         ▼
                    Frontend UI
```

---

## 🤖 AI Workflow

BizNest uses operational business data to generate intelligence.

```text
Sales / Inventory Data
        ↓
   PostgreSQL
        ↓
   Data Extraction
        ↓
 Data Preprocessing
        ↓
 Machine Learning Model
        ↓
 Predictions / Analysis
        ↓
 Business Recommendations
```

Examples of AI-driven functionality:

**Demand Prediction**
```text
Historical Sales
      ↓
Feature Preparation
      ↓
Random Forest Model
      ↓
Predicted Demand
      ↓
Restock Recommendation
```

**Revenue Forecasting**
```text
Historical Revenue
      ↓
Data Analysis / Model
      ↓
Forecast
      ↓
Business Planning
```

---

## 🔌 Services & Ports

| Service | Technology | Port |
|---|---|---:|
| Frontend | React + Vite | `5173` |
| Backend | Spring Boot | `8080` |
| AI Service | Python + FastAPI | `8000` |
| Database | PostgreSQL | `5432` |

---

## 🧪 API Testing

Backend REST APIs can be tested using **Postman**.

Typical API areas include:

```text
Authentication
Products
Inventory / Stock
Sales
Purchases
Customers
Payments
Staff
Dashboard
AI Services
```

For development, verify the backend is running before sending requests from Postman.

---

## 📁 Backend Architecture

The Spring Boot backend follows a layered architecture:

```text
Controller
    ↓
Service
    ↓
Repository
    ↓
Entity
    ↓
PostgreSQL
```

### Controller
Handles HTTP requests and responses.

### Service
Contains business logic.

### Repository
Handles database operations through Spring Data JPA.

### Entity
Represents database tables and domain objects.

This separation makes the backend easier to maintain, test, and extend.

---

## 🎯 Project Goals

BizNest aims to:

- Centralize shop operations in one platform
- Reduce manual inventory and payment tracking
- Provide real-time business visibility
- Simplify staff and operational management
- Help businesses understand sales patterns
- Provide AI-assisted demand and revenue insights
- Support better inventory planning through data

---

## 🔮 Future Improvements

Potential areas for further development include:

- Advanced sales forecasting
- More detailed financial analytics
- Automated purchase recommendations
- Advanced customer segmentation
- Multi-store support
- Notifications for critical stock levels
- More ML models and automated model evaluation
- Cloud deployment
- Automated backups and monitoring
