# Bibliook System Architecture

## 1. Overview

Bibliook is an AI-powered reference and bibliography management platform designed to enhance academic productivity. It leverages machine learning and generative AI to validate, format, and enrich bibliographic data, providing seamless integration between frontend interfaces, backend services, inference models, and external AI APIs.

---

## 2. System Components

### 2.1 Frontend

The frontend is built using **Next.js** for the web and **React Native** for mobile applications. It provides an intuitive UI for managing references, validating entries, and generating citations using AI assistance. It communicates with backend APIs over HTTPS and manages local state using **Redux Toolkit** for optimal performance.

### 2.2 Backend

The backend is developed using **Node.js (Express.js)** and handles all business logic, authentication, and API orchestration. It manages user data, bibliography entries, and orchestrates calls to the AI inference server and external APIs. Key features include:

- Rate limiting
- Caching
- JWT-based authentication for secure user management

### 2.3 AI Inference Server

The inference server hosts custom-trained ML models built in **Python** using frameworks such as **TensorFlow**, **Scikit Learn** or **PyTorch**. These models include the **Biblio Name Validator**, which checks the validity and structure of bibliographic names. The server exposes RESTful endpoints via **FastAPI**, which the backend queries to obtain predictions and insights.

### 2.4 Generative AI Integration

Bibliook integrates with external generative AI providers such as **OpenAI** or **Gemini** for:

- Question answer generation
- Editor Guide
- Reference suggestions

The backend sends structured prompts containing user queries or metadata, and the model returns formatted, context-aware responses. The system uses asynchronous task handling to prevent API bottlenecks.

### 2.5 Database Layer

The data layer uses **MySQL** and **MongoDB** for relational storage and **Redis** for caching. It stores:

- User profiles
- Biblios
- Chapters
- Questions and Answers
- User Preferences
- AI model logs
- Feedback

Data validation and migrations are managed using **MySQL ORM** for maintainability and scalability.

---

## 3. Data Flow

1. A user interacts from frontend.
2. The backend validates the request and send response.
3. Also, the backend validates and sends the data to the AI inference API.
4. The inference server processes the data through the ML model.
5. The backend receives the result and optionally enhances it using a Generative AI API.
6. The response is stored in the database and returned to the frontend for visualization.

---

## 4. Deployment and Infrastructure

Bibliook uses a microservices-based deployment on cloud providers like **Vercel** and **Render**:

- **Frontend:** Deployed on **Vercel**.
- **Backend:** Hosted on **Render**.
- **Inference Server:** Deployed via **Hugging Face Spaces**.
- **Database:** Managed **MySQL**.

CI/CD pipelines automate deployment, testing, and versioning.

---

## 5. Security Considerations

The system enforces:

- **HTTPS**
- **JWT authentication**
- **Rate limiting**
- **Input sanitization**
- **Access control layers**
- **Encryption**

Environment secrets are stored securely using environment variables or cloud secret managers. All external API keys are isolated per environment (development, staging, production).

---

© 2025 Bibliook | Authored by Ashish Sigdel
