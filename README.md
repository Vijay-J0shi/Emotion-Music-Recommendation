# Emotion-Based Music Recommender

A Flask-based web application that detects a user's emotion through facial recognition using a webcam and recommends music from YouTube and Spotify based on the detected emotion. The app also includes features like a focus timer, to-do list, voice search, and the ability to like and save songs.

## Table of Contents
- [Project Description](#project-description)
- [Features](#features)
- [Technologies Used](#technologies-used)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Environment Variables](#environment-variables)
- [Usage](#usage)
- [File Structure](#file-structure)
- [Contributing](#contributing)
- [License](#license)

## Project Description
The Emotion-Based Music Recommender is a web application designed to enhance the user's music listening experience by recommending songs based on their current emotional state. It uses a pre-trained deep learning model to detect emotions from facial expressions captured via a webcam. Based on the detected emotion (e.g., happy, sad, angry), the app fetches music recommendations from YouTube and Spotify. Additional features include a focus timer for productivity, a to-do list, voice search for songs, and the ability to save liked songs.

## Features
- **Emotion Detection**: Uses a pre-trained model (`emotion_model.h5`) and OpenCV's Haar Cascade for face detection to identify emotions from webcam feed.
- **Music Recommendations**: Fetches music playlists from YouTube and Spotify based on the detected emotion or user search queries.
- **Webcam Integration**: Real-time webcam feed to capture and analyze facial expressions.
- **Voice Search**: Allows users to search for songs or artists using voice input.
- **Focus Timer**: A stopwatch-style timer to help users track focus time.
- **To-Do List**: A simple to-do list with add, edit, delete, and mark-as-complete functionality.
- **Liked Songs**: Users can like and save songs to a persistent list.
- **Theme Toggle**: Switch between dark and light themes for better user experience.
- **Emotion History**: Displays a bar chart of detected emotions over time using Chart.js.

## Technologies Used
- **Backend**:
  - Python 3.x
  - Flask (web framework)
  - OpenCV (for webcam and face detection)
  - TensorFlow/Keras (for loading and using the emotion detection model)
  - Google API Client (for YouTube API)
  - Spotipy (for Spotify API)
- **Frontend**:
  - HTML, CSS, JavaScript
  - Chart.js (for emotion history visualization)
  - Font Awesome (for icons)
  - Google Fonts (Poppins)
- **Other**:
  - HTTPS support with self-signed SSL certificates (`cert.pem`, `key.pem`)
  - JSON for storing liked videos
  - LocalStorage for persisting to-do list and emotion history

## Prerequisites
Before running the project, ensure you have the following installed:
- Python 3.8 or higher
- pip (Python package manager)
- A webcam for emotion detection
- A modern web browser (Chrome, Firefox, etc.) with microphone access for voice search

## Installation
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-username/emotion-based-music-recommender.git
   cd emotion-based-music-recommender
   ```

2. **Set Up a Virtual Environment** (optional but recommended):
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install Dependencies**:
   Install the required Python packages listed in `requirements.txt`:
   ```bash
   pip install -r requirements.txt
   ```

4. **Generate SSL Certificates** (for HTTPS):
   The app runs with HTTPS, so you need SSL certificates. You can generate self-signed certificates using OpenSSL:
   ```bash
   openssl req -x509 -newkey rsa:4096 -nodes -out cert.pem -keyout key.pem -days 365
   ```
   Place `cert.pem` and `key.pem` in the project root directory.

5. **Set Up Environment Variables**:
   Create a `.env` file in the project root and add the following:
   ```plaintext
   YOUTUBE_API_KEY=your-youtube-api-key
   SPOTIFY_CLIENT_ID=your-spotify-client-id
   SPOTIFY_CLIENT_SECRET=your-spotify-client-secret
   USER_REGION=US  # Optional: Set your region (e.g., US, IN)
   ```
   - **YouTube API Key**: Get from [Google Cloud Console](https://console.cloud.google.com/).
   - **Spotify Client ID and Secret**: Get from [Spotify Developer Dashboard](https://developer.spotify.com/dashboard/).

6. **Download the Emotion Model**:
   Ensure the `emotion_model.h5` file (pre-trained emotion detection model) is in the project root directory. If you don't have this model, you may need to train one using a dataset like FER2013 or download a compatible model.

7. **Download Haar Cascade File**:
   The app uses OpenCV's Haar Cascade for face detection (`haarcascade_frontalface_default.xml`). This file is typically included with OpenCV, but ensure it's accessible in the OpenCV data directory.

## Environment Variables
The following environment variables are required in the `.env` file:
- `YOUTUBE_API_KEY`: API key for accessing the YouTube Data API.
- `SPOTIFY_CLIENT_ID`: Client ID for Spotify API.
- `SPOTIFY_CLIENT_SECRET`: Client Secret for Spotify API.
- `USER_REGION`: (Optional) Region code for content filtering (e.g., `US`).

## Usage
1. **Run the Application**:
   Start the Flask server:
   ```bash
   python app.py
   ```
   The app will run on `https://localhost:5000`. Since it uses a self-signed certificate, your browser may show a security warning—proceed by accepting the certificate.

2. **Access the App**:
   Open your browser and navigate to `https://localhost:5000`.

3. **Using the App**:
   - **Emotion Detection**: Click "Start Camera" to activate the webcam, then "Capture Image" to detect your emotion.
   - **Music Recommendations**: Based on the detected emotion, the app will display YouTube and Spotify recommendations. Click the play button to listen.
   - **Search**: Use the search bar or voice search to find specific songs or artists.
   - **Focus Timer**: Start the timer to track your focus time.
   - **To-Do List**: Add, edit, or delete tasks from the to-do panel.
   - **Like Songs**: Click the heart icon to save songs to your liked list.
   - **Theme Toggle**: Switch between dark and light themes.

4. **Stop the App**:
   Press `Ctrl+C` in the terminal to stop the Flask server.

## File Structure
```
emotion-based-music-recommender/
│
├── static/                     # Static files (CSS, images)
│   ├── face_logo.jpg           # Face logo for webcam placeholder
│   ├── face_logo.png           # Alternative face logo
│   ├── josh_emo_musics_logo.png # App logo
│   └── style.css               # CSS styles
│
├── templates/                  # HTML templates
│   └── index.html              # Main HTML page
│
├── .cache/                     # Cache directory (auto-generated)
├── .env                        # Environment variables
├── app.py                      # Main Flask application
├── cert.pem                    # SSL certificate
├── emotion_model.h5            # Pre-trained emotion detection model
├── haarcascade_frontalface_default.xml # Haar Cascade for face detection
├── key.pem                     # SSL private key
├── liked_videos.json           # JSON file for storing liked videos
└── requirements.txt            # Python dependencies
```

## Contributing
Contributions are welcome! To contribute:
1. Fork the repository.
2. Create a new branch (`git checkout -b feature/your-feature`).
3. Make your changes and commit (`git commit -m "Add your feature"`).
4. Push to your branch (`git push origin feature/your-feature`).
5. Open a pull request.

Please ensure your code follows the project's coding style and includes appropriate documentation.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
```

---

### Project Description

#### Emotion-Based Music Recommender

The **Emotion-Based Music Recommender** is a web application that leverages facial recognition and emotion detection to recommend music tailored to the user's current emotional state. Built using Flask, the app integrates with a webcam to capture the user's facial expression, processes it using a pre-trained deep learning model (`emotion_model.h5`), and detects emotions such as happy, sad, angry, or neutral. Based on the detected emotion, the app fetches music recommendations from YouTube and Spotify using their respective APIs.

The application goes beyond simple music recommendations by offering a suite of productivity and user engagement features. Users can search for songs manually or via voice input, track their focus time with a built-in timer, manage tasks with a to-do list, and save their favorite songs. The interface is user-friendly, with a dark/light theme toggle, a responsive design, and an emotion history chart to visualize past detections.

#### Key Features:
1. **Emotion Detection**:
   - Uses OpenCV for face detection with the Haar Cascade classifier (`haarcascade_frontalface_default.xml`).
   - Employs a pre-trained Keras model (`emotion_model.h5`) to classify emotions into categories like angry, disgust, fear, happy, sad, surprise, and neutral.
   - Captures images from the webcam and processes them in real-time.

2. **Music Recommendations**:
   - Maps detected emotions to music genres (e.g., happy → pop, sad → blues) and fetches relevant playlists from YouTube and Spotify.
   - Supports manual search for songs or artists, with results displayed from both platforms.

3. **Webcam Integration**:
   - Provides a live webcam feed for capturing facial expressions.
   - Includes a placeholder logo (`face_logo.png`) when the camera is inactive.

4. **Voice Search**:
   - Utilizes the Web Speech API to enable voice-based search for songs or artists.
   - Handles errors like microphone access denial gracefully.

5. **Focus Timer**:
   - A stopwatch-style timer to help users track their focus or productivity time.
   - Persists the total time in `localStorage` for continuity across sessions.

6. **To-Do List**:
   - Allows users to add, edit, delete, and mark tasks as complete.
   - Persists tasks in `localStorage` for durability.

7. **Liked Songs**:
   - Users can like songs, which are saved to a `liked_videos.json` file.
   - Displays a list of liked songs with links to play them.

8. **Emotion History**:
   - Tracks detected emotions over time and visualizes them in a bar chart using Chart.js.
   - Stores history in `localStorage` for persistence.

9. **Theme Toggle**:
   - Supports dark and light themes with smooth transitions.
   - Uses CSS gradients and background patterns for a visually appealing design.

#### Technologies Used:
- **Backend**: Flask, OpenCV, TensorFlow/Keras, Google API Client (YouTube), Spotipy (Spotify)
- **Frontend**: HTML, CSS, JavaScript, Chart.js, Font Awesome, Google Fonts
- **Other**: HTTPS with self-signed SSL certificates, JSON for data persistence, LocalStorage for client-side storage

#### How It Works:
1. The user starts the webcam feed and captures an image.
2. The app detects the user's emotion using the pre-trained model.
3. Based on the emotion, it fetches music recommendations from YouTube and Spotify.
4. The user can play recommended songs, search for others, like songs, manage tasks, and track focus time.
5. The app provides a seamless experience with a modern UI, theme options, and productivity tools.

#### Future Improvements:
- Add support for more music platforms (e.g., Apple Music, SoundCloud).
- Improve emotion detection accuracy with a more advanced model or real-time video analysis.
- Implement user authentication to save liked songs and to-do lists per user.
- Add playlist creation and sharing features.
- Enhance the UI with more interactive elements and animations.

This project combines AI, web development, and API integration to create a unique and engaging music recommendation experience, making it a great tool for both entertainment and productivity.

---

Let me know if you'd like to expand on any section or need further assistance!
