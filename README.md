# Emotion-Based Music Recommender

This is a Flask-based web application that detects a user’s emotion using facial recognition through a webcam and recommends music from YouTube and Spotify based on the detected emotion. It includes additional features such as a focus timer, to-do list, voice search, and the ability to save liked songs.

## Table of Contents
- [Project Overview](#project-overview)
- [Key Features](#key-features)
- [Technologies Utilized](#technologies-utilized)
- [Prerequisites](#prerequisites)
- [Installation Guide](#installation-guide)
- [Environment Configuration](#environment-configuration)
- [Usage Instructions](#usage-instructions)
- [Directory Structure](#directory-structure)
- [Contribution Guidelines](#contribution-guidelines)

## Project Overview
The Emotion-Based Music Recommender is a web application designed to analyze a user’s emotional state using a webcam and suggest music that matches their mood. It employs a pre-trained deep learning model to detect emotions such as happiness, sadness, or anger from facial expressions. The application integrates with YouTube and Spotify APIs to fetch relevant music recommendations. Additional utilities like a focus timer, to-do list, and voice search enhance its functionality.

## Key Features
- **Emotion Detection**: Utilizes a webcam to capture facial expressions and a pre-trained model (`emotion_model.h5`) to classify emotions.
- **Music Recommendations**: Retrieves playlists from YouTube and Spotify based on the detected emotion or user queries.
- **Webcam Integration**: Provides real-time video feed for emotion analysis.
- **Voice Search**: Enables song searches through voice commands using the Web Speech API.
- **Focus Timer**: Tracks time for productivity or study sessions.
- **To-Do List**: Supports task management with add, edit, and delete functionalities.
- **Liked Songs**: Allows users to save favorite songs in a persistent list.
- **Theme Switching**: Offers dark and light themes for user preference.
- **Emotion History**: Displays a graphical representation of detected emotions over time using Chart.js.

## Technologies Utilized
- **Backend**:
  - Python 3.x: Core programming language.
  - Flask: Web framework for server-side logic.
  - OpenCV: Handles webcam input and face detection.
  - TensorFlow/Keras: Loads and processes the emotion detection model.
  - Google API Client: Integrates YouTube Data API.
  - Spotipy: Connects to Spotify API.
- **Frontend**:
  - HTML, CSS, JavaScript: Constructs the user interface.
  - Chart.js: Visualizes emotion history.
  - Font Awesome: Provides icons.
  - Google Fonts: Enhances typography with the Poppins font.
- **Additional Tools**:
  - HTTPS: Ensures secure communication with self-signed SSL certificates.
  - JSON: Stores liked songs data.
  - LocalStorage: Persists to-do list and emotion history on the client side.

## Prerequisites
To run this application, ensure the following are available:
- Python 3.8 or higher.
- pip (Python package manager).
- A functional webcam.
- A modern web browser (e.g., Chrome, Firefox) with microphone access.

## Installation Guide
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-username/emotion-based-music-recommender.git
   cd emotion-based-music-recommender
   ```

2. **Set Up a Virtual Environment** (Recommended):
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install Dependencies**:
   Execute the following command to install required packages:
   ```bash
   pip install -r requirements.txt
   Train emotion-based-model-prediction.ipynb to download emotion_model.ph model ,it will save automatically, just place it in right place
   ```

4. **Generate SSL Certificates**:
   For HTTPS support, create self-signed certificates using OpenSSL:
   ```bash
   openssl req -x509 -newkey rsa:4096 -nodes -out cert.pem -keyout key.pem -days 365
   ```
   Place `cert.pem` and `key.pem` in the project root.

5. **Configure Environment Variables**:
   Create a `.env` file in the root directory with the following:
   ```plaintext
   YOUTUBE_API_KEY=your-youtube-api-key
   SPOTIFY_CLIENT_ID=your-spotify-client-id
   SPOTIFY_CLIENT_SECRET=your-spotify-client-secret
   USER_REGION=IN  # Optional: Specify your region (e.g., IN for India)
   ```
   - Obtain `YOUTUBE_API_KEY` from [Google Cloud Console](https://console.cloud.google.com/).
   - Obtain `SPOTIFY_CLIENT_ID` and `SPOTIFY_CLIENT_SECRET` from [Spotify Developer Dashboard](https://developer.spotify.com/dashboard/).

6. **Acquire the Emotion Model**:
   Ensure the `emotion_model.h5` file is present in the root directory. This pre-trained model is required for emotion detection.

7. **Obtain Haar Cascade File**:
   The `haarcascade_frontalface_default.xml` file, used for face detection, should be available (typically bundled with OpenCV).

## Environment Configuration
The `.env` file must include:
- `YOUTUBE_API_KEY`: API key for YouTube integration.
- `SPOTIFY_CLIENT_ID`: Client ID for Spotify API.
- `SPOTIFY_CLIENT_SECRET`: Client Secret for Spotify API.
- `USER_REGION`: Optional region code (e.g., `IN` for India).

## Usage Instructions
1. **Launch the Application**:
   Run the Flask server with:
   ```bash
   python app.py
   ```
   The application will be accessible at `https://localhost:5000`. Accept the self-signed certificate warning in your browser.

2. **Access the Application**:
   Open a browser and navigate to `https://localhost:5000`.

3. **Interact with Features**:
   - Start the webcam and capture an image to detect your emotion.
   - View and play music recommendations based on your mood.
   - Use voice or text search to find specific songs.
   - Track time with the focus timer.
   - Manage tasks in the to-do list.
   - Save songs by liking them.
   - Toggle between dark and light themes.

4. **Stop the Application**:
   Press `Ctrl+C` in the terminal to terminate the server.

## Directory Structure
```
emotion-based-music-recommender/
├── static/                     # Static assets
│   ├── face_logo.jpg           # Webcam placeholder image
│   ├── face_logo.png           # Alternative placeholder
│   ├── josh_emo_musics_logo.png # Application logo
│   └── style.css               # Styling rules
├── templates/                  # HTML templates
│   └── index.html              # Primary webpage
├── .env                        # Environment variables
├── app.py                      # Core Flask application
├── cert.pem                    # SSL certificate
├── emotion_model.h5            # Emotion detection model
├── haarcascade_frontalface_default.xml # Face detection classifier
├── key.pem                     # SSL private key
├── liked_videos.json           # Liked songs storage
└── requirements.txt            # Dependency list
```

## Contribution Guidelines
Contributions are appreciated. To contribute:
1. Fork the repository.
2. Create a feature branch (`git checkout -b feature/your-contribution`).
3. Commit changes (`git commit -m "Implemented feature"`).
4. Push to your branch (`git push origin feature/your-contribution`).
5. Submit a pull request on GitHub.
