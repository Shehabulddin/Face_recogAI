# Face\_recogAI

A facial recognition application for collecting, analyzing, and serving real-time face analysis including age, gender, and emotion detection.

## Features

* **Data Collection**: Capture face images via webcam and extract age, gender, and emotion data using DeepFace.
* **Benchmark Analysis**: Generate CSV reports and visualize gender and emotion distribution, and average age of collected samples.
* **Real-Time API**: Serve face recognition endpoints via a FastAPI server with WebSocket support.
* **Dockerized Deployment**: Build and run the application in a Docker container for easy setup.

## Prerequisites

* Python 3.12 or higher


## Getting Started

### Clone the Repository

```bash
git clone https://github.com/Shehabulddin/Face_recogAI.git
cd Face_recogAI
```

### Environment Variables

Copy the template and set your credentials:

```bash
cp .env.template .env
# Edit .env with your desired username and password
```

### Install Dependencies

#### Using Poetry

```bash
poetry install
```

#### Using Pip

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

## Usage

### 1. Collect Face Data

Run the data collector and analyzer script to capture up to 30 samples and generate benchmarks:

```bash
python face_data_collector_and_analyzer.py
```

This will:

* Launch your webcam and collect face data (age, gender, emotion).
* Save results to `collected_face_data.csv`.
* Compute distribution statistics and average age.
* Generate `gender_benchmark.png` and `emotion_benchmark.png`.

### 2. Start the API Server

Launch the FastAPI server to serve real-time face recognition:

```bash
uvicorn src.server:app --host 0.0.0.0 --port 8000 --reload
```

* **HTTP Basic Auth** is enabled. Use the credentials from your `.env` file.
* **WebSocket endpoint** available at `/ws` for streaming face analysis.

### 3. Docker Deployment

Build the Docker image:

```bash
docker build -t face_recogai .
```

Run the container:

```bash
docker run -d -p 8000:8000 --name face_recogai face_recogai
```

