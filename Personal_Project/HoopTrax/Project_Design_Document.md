# Project Design Document (PDD)  
## HoopTrax: NBA Performance Prediction & Analysis App

---

## 1. Project Overview

**HoopTrax** is an application designed to predict NBA player performance (e.g., points per game, assists, rebounds) using historical data and user-provided inputs. The app integrates model training, an interactive web interface, prediction logging, and containerized deployment. Its core functionality leverages two primary datasets:  
- **Tracking Data** – High-frequency positional and event data for players.  
- **Play-by-Play (PBPSTATS) Data** – Detailed game event information.

---

## 2. Objectives

- **Predictive Analytics:**  
  Develop regression or classification models (using frameworks like PyTorch or TensorFlow) to forecast player performance metrics.

- **Interactive User Interface:**  
  Provide a user-friendly Streamlit-based web application for users to input parameters and view predictions in real time.

- **Prediction Logging:**  
  Log every prediction along with input features, timestamps, and (optionally) actual outcomes in a PostgreSQL database.

- **Deployment:**  
  Containerize the application using Docker (or Docker Compose) to ensure easy deployment and scalability.

---

## 3. Scope

- **In-Scope:**  
  - Data preprocessing and feature engineering from Tracking and PBPSTATS datasets.  
  - Model training for performance prediction and Expected Possession Value (EPV) analysis.  
  - Web interface development (using Streamlit) and prediction logging via a PostgreSQL database.  
  - Containerized deployment.

- **Out-of-Scope:**  
  - Integration of additional datasets (e.g., SHOTDETAIL, NBASTATS) is deferred until core functionality is established.  
  - Advanced front-end design beyond the basic interactive dashboard.

---

## 4. Requirements

### 4.1 Functional Requirements
- **Data Processing:**  
  - Load raw tracking and play-by-play data.  
  - Clean data, handle missing values, and compute derived features (e.g., time differences, spatial differences, velocity).

- **Modeling:**  
  - Train predictive models to estimate player performance.  
  - Evaluate model performance using appropriate metrics.

- **User Interface:**  
  - Streamlit app to allow users to enter game context and view predictions.  
  - Display prediction results along with model confidence and historical logs.

- **Prediction Logging:**  
  - Store each prediction in a PostgreSQL database including input features, predicted values, and timestamps.

### 4.2 Non-Functional Requirements
- **Scalability & Maintainability:**  
  - Modular code design and clear separation between data processing, modeling, and interface code.
  
- **Performance:**  
  - Fast prediction times and responsive web interface.
  
- **Security:**  
  - Secure data transmission between the web app and the database.
  
- **Deployment:**  
  - Use Docker for consistent environment replication and easy deployment.

---

## 5. System Architecture & Modules

### 5.1 Overall Architecture Diagram

```mermaid
flowchart TD
    A[Raw Data: Tracking & PBPSTATS] --> B[Data Processing & Feature Engineering]
    B --> C[Integrated Dataset]
    C --> D[Model Training (EPV, performance predictions)]
    D --> E[Prediction Logging (PostgreSQL)]
    D --> F[Streamlit Web App]
    F --> E
```

### 5.2 Modules Description
- **Data Processing:**  
  Scripts and notebooks for cleaning raw data and engineering features such as time differences, spatial differences, Euclidean distance, and velocity.

- **Integration:**  
  Code to merge tracking and play-by-play datasets (using common identifiers like game IDs and timestamps).

- **Modeling:**  
  Training modules (e.g., EPV model) that consume the processed data and output predictions.

- **User Interface:**  
  A Streamlit application that accepts user inputs, displays predictions, and fetches historical logs.

- **Prediction Logging:**  
  A PostgreSQL database to record each prediction along with its associated metadata.

---

## 6. Technologies Used

- **Programming Language:** Python  
- **Data Processing/ML Frameworks:** Pandas, NumPy, PyTorch/TensorFlow  
- **Web Framework:** Streamlit  
- **Database:** PostgreSQL  
- **Containerization:** Docker, Docker Compose  
- **Visualization:** Matplotlib, Seaborn, Plotly  
- **Version Control:** Git

---

## 7. Database Design & ERD (Overview)

Our database will primarily consist of two tables:

- **PLAYER Table:**  
  Stores static player information (Player_ID, Name, Team, Position).

- **PREDICTION Table:**  
  Logs each prediction along with:
  - Timestamp  
  - Reference to Player_ID  
  - Serialized Input_Features  
  - Predicted performance metrics (points, assists, rebounds)  
  - (Optional) Actual performance values  
  - Model confidence score

For a detailed diagram, please refer to the Engineering Requirements Document.

---

## 8. Deployment & Integration

- **Containerization:**  
  The app (including the web interface and the PostgreSQL database) will be containerized using Docker and orchestrated with Docker Compose.

- **Integration:**  
  Reusable modules (in the `src/` directory) support data processing, feature engineering, and integration between the tracking and PBPSTATS datasets.

---

## 9. Future Enhancements

- Incorporate additional datasets (e.g., SHOTDETAIL, NBASTATS) to further enhance predictive capability.
- Extend the web interface with more detailed visual analytics and user feedback mechanisms.
- Refine model explainability (using tools like SHAP or LIME).

---

## 10. Final Thoughts

This PDD outlines the vision, objectives, and high-level system design for HoopTrax. It provides a clear roadmap for developing a robust, scalable, and maintainable application that leverages high-frequency tracking data and contextual play-by-play information to predict NBA player performance.