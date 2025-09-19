# TrackIt

A Flask-based CRUD web application to manage learning topics and subtopics.  
TrackIt allows users to create, edit, delete, and track the completion status of subtopics, with secure authentication and AWS DynamoDB as the backend.

---

##  Features
  **User Authentication**  
  - Secure signup and login using bcrypt password hashing.  
  - Session management with Flask and environment-based secrets.  

  **Topic & Subtopic Management**  
  - Create topics with multiple subtopics.  
  - Edit or delete topics and subtopics.  
  - Toggle subtopic completion status (done/undone).  

  **Cloud-Native Backend**  
  - Built with AWS DynamoDB using a single-table design (PK/SK model).  
  - Serverless deployment using AWS Lambda, API Gateway, and [Zappa](https://github.com/zappa/Zappa).  

  **Frontend**  
  - Responsive interface using Jinja2 templates and Bootstrap.  
  - Forms validated with Flask-WTF & WTForms (with CSRF protection).  

---

##  Tech Stack
- **Backend:** Flask, Flask-WTF, bcrypt  
- **Frontend:** Jinja2, Bootstrap  
- **Database:** AWS DynamoDB  
- **Deployment:** AWS Lambda + API Gateway via Zappa  
- **Other:** Python 3.12, dotenv for local config  

---

##  Getting Started

### Prerequisites
- Python 3.12  
- AWS CLI configured with your account  
- DynamoDB table (single-table design, set via `.env`)  
- [Zappa](https://github.com/zappa/Zappa) installed (`pip install zappa`)  

### 1. Clone the repository
```bash
git clone https://github.com/neelspatel02/trackit.git
cd trackit
```

### 2. Create a virtual environment
```bash
python -m venv .venv
source .venv/bin/activate   # Linux/Mac
.venv\Scripts\activate      # Windows
```

### 3. Install dependencies
```bash
pip install -r requirements.txt
```

### 4. Setup environment variables
Create a `.env` file:
```ini
AWS_REGION=us-east-1
DYNAMODB_TABLE=TrackItTable
SECRET_KEY=your-secret-key
```

### 5. Run locally
```bash
python app.py
```
App will be available at `http://127.0.0.1:5000`.

---

## ☁️ Deployment with Zappa
1. Initialize Zappa:
   ```bash
   zappa init
   ```
   (or use the provided `zappa_settings.json`)

2. Deploy to AWS:
   ```bash
   zappa deploy dev
   ```

3. Update after changes:
   ```bash
   zappa update dev
   ```

---

## 🔒 Security Notes
- Passwords are hashed with bcrypt before storage.  
- Flask sessions secured with environment `SECRET_KEY`.  
- IAM policy restricted to a single DynamoDB table (least privilege).  
- CSRF protection enabled for all forms.  

---




---

## 📌 Project Status
TrackIt is a learning project showcasing:
- CRUD operations in Flask  
- Integration with AWS services  
- Secure authentication & deployment practices  

---

##  License
MIT License
