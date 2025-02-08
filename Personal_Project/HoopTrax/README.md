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
- Alternatively, Python 3.8+ if running locally.

### Clone the Repository
```bash
git clone https://github.com/yourusername/hooptrax.git
cd hooptrax
```

### Creating a Virtual Environment (Optional)
Creating a virtual environment is a best practice to isolate your project dependencies.

1. **Create the Virtual Environment:**
   ```bash
   python -m venv venv
   ```

2. **Activate the Virtual Environment:**
   - **On macOS/Linux:**
     ```bash
     source venv/bin/activate
     ```
   - **On Windows:**
     ```bash
     venv\Scripts\activate
     ```

### Installing Dependencies
Once your virtual environment is activated, install the required libraries:
```bash
pip install -r requirements.txt
```

## Usage

To run the application, use the following command:
```bash
docker-compose up
```

## Project Structure

The project is organized as follows:
- `app/`: Contains the Streamlit application code.
- `data/`: Contains raw data and processed datasets.
- `models/`: Contains trained machine learning models.
- `scripts/`: Contains utility scripts for data processing and model training.
- `tests/`: Contains unit tests for the application.

## Documentation

For more detailed information about the project architecture, data processing, and feature engineering, refer to the [Documentation](Documentation) directory.

## Contributing

We welcome contributions from the community! Please read the [Contributing Guidelines](CONTRIBUTING.md) for more information on how to contribute to the project.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more information.

## Contact

For any questions or inquiries, please contact us at [contact@hooptrax.com](mailto:contact@hooptrax.com).
