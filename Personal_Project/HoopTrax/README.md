# HoopTrax: NBA Performance Prediction & Analysis App

HoopTrax is a predictive analytics application designed to forecast NBA player performance metrics such as points, assists, and rebounds per game. By integrating high-frequency tracking data and play-by-play data, the app leverages advanced data processing, feature engineering, and machine learning modeling to provide actionable insights. The interactive Streamlit web interface makes it easy for analysts, coaches, and fans to visualize and access predictions in real time.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Architecture](#architecture)
- [Installation & Setup](#installation--setup)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Documentation](#documentation)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Overview

HoopTrax harnesses both player tracking and play-by-play datasets to provide a robust prediction model for NBA performance. The application is containerized with Docker and orchestrated using Docker Compose to ensure consistency across various environments. It logs every prediction along with input features, timestamps, and (optionally) actual game outcomes in a PostgreSQL database for further analysis.

## Features

- **Data Processing:**  
  - Cleans raw tracking and play-by-play data.
  - Implements feature engineering (time differences, spatial metrics, Euclidean distance, velocity, etc.).

- **Predictive Modeling:**  
  - Contains modules (like the EPV model) that train on the processed data.
  - Evaluates and logs predictions for insightful analysis.

- **Interactive Web Interface:**  
  - A Streamlit-based dashboard for real-time data input and visual display of predictions.

- **Containerized Deployment:**  
  - Docker and Docker Compose make it easy to build, test, and deploy the application along with its PostgreSQL database.

## Architecture

The system is divided into several key layers:
- **Data Ingestion & Processing:** Handles the loading, cleaning, and preprocessing of raw data.
- **Integration & Modeling:** Merges datasets and builds the predictive models.
- **Application & Presentation:** Offers a user-friendly interface for interacting with predictions.
- **Deployment:** Utilizes containerization for consistent deployment across environments.

For a visual representation, refer to the ER Diagram in the [Documentation/ERD.md](Documentation/ERD.md) file.

## Installation & Setup

### Prerequisites
- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/install/)
- Alternatively, Python 3.8+ and the libraries in `requirements.txt` if running locally.

### Clone the Repository
