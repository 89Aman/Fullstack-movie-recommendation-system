# Fullstack Movie Recommendation System

A fullstack movie recommendation system built with **TensorFlow Recommenders** and **Flutter**, demonstrating a modern approach to personalized movie recommendations.

## Features

- **Two-stage recommendation pipeline** — Retrieval and ranking models for accurate predictions
- **TensorFlow Serving** — Production-ready model deployment
- **Flutter frontend** — Cross-platform UI for iOS, Android, web, and desktop
- **Flask backend** — Lightweight API orchestrating model inference

## Tech Stack

| Layer    | Technology                     |
| -------- | ------------------------------ |
| Frontend | Flutter, Dart                  |
| Backend  | Flask, Python                  |
| ML       | TensorFlow Recommenders, Keras |
| Serving  | TensorFlow Serving             |

## Project Structure

```
├── finished/
│   ├── backend/
│   │   ├── recommender.py      # Flask API server
│   │   ├── models.config       # TensorFlow Serving config
│   │   ├── retrieval/          # Retrieval model + notebook
│   │   └── ranking/            # Ranking model + notebook
│   └── frontend/
│       └── lib/main.dart       # Flutter app
└── codelab_rebuild.yaml        # Codelab build script
```

## Getting Started

### Prerequisites

- Python 3.8+
- Flutter SDK
- Docker (for TensorFlow Serving)

### Backend Setup

1. Start TensorFlow Serving with the models:

   ```bash
   docker run -t --rm -p 8501:8501 \
     -v "$(pwd)/finished/backend:/models" \
     tensorflow/serving:2.14.0 --model_config_file=/models/models.config
   ```

2. Install Python dependencies and run the Flask server:

   ```bash
   cd finished/backend
   pip install flask flask-cors numpy requests
   python recommender.py
   ```

   The API will be available at `http://localhost:5000`.

### Frontend Setup

1. Navigate to the frontend directory:

   ```bash
   cd finished/frontend
   ```

2. Install dependencies and run:

   ```bash
   flutter pub get
   flutter run
   ```

## Usage

1. Enter a user ID in the text field
2. Click **Recommend** to get personalized movie suggestions
3. View the ranked list of recommended movies

## API Reference

### `POST /recommend`

Request body:

```json
{ "user_id": "42" }
```

Response:

```json
{ "movies": ["Movie A", "Movie B", "Movie C", ...] }
```

## Resources

- [TensorFlow Recommenders](https://www.tensorflow.org/recommenders)
- [Flutter Documentation](https://docs.flutter.dev/)

## License

This project is for educational purposes.
