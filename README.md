# Emotion-based-music-player
🎵 Emotion-Based Music Player An intelligent desktop application that detects your emotional state through facial expressions or voice input and plays music that matches your mood using YouTube. Built with Python, DeepFace, Google API, and a sleek Tkinter GUI.

📌 Features

🎭 Facial Emotion Detection: Captures your face via webcam and analyzes your emotion using DeepFace.
🗣 Voice Prompt Recognition: Listens to your voice and interprets the emotional tone of your spoken words.
🔍 Smart Music Mapping: Maps detected emotions to curated music keywords.
▶️ YouTube Music Playback: Automatically opens a matching music video on YouTube using the YouTube Data API.
🖼️ Dynamic GUI: Fullscreen Tkinter interface with responsive background and real-time webcam preview.

🚀 How It Works

Launch the application.
Choose between:
Capture Emotion: Uses your webcam to detect your facial emotion.
Voice Prompt: Uses your microphone to capture and interpret your spoken mood.
The app maps the detected emotion to a music genre or mood.
It fetches a relevant music video from YouTube and plays it in your browser.

🧠 Emotion-to-Music Mapping | Emotion | Music Style | | Happy | Upbeat Songs | | Sad | Sad Acoustic Songs | | Angry | Angry Rock/Metal Music | | Surprise | Surprising Energetic Music | | Neutral | Chill Ambient Music | | Fear | Calming Instrumental Music | | Disgust | Grunge/Alternative Music |

🛠️ Tech Stack

Python 3.x
Tkinter – GUI framework
OpenCV – Webcam integration
DeepFace – Facial emotion recognition
SpeechRecognition – Voice input handling
Google API Client – YouTube Data API v3
Pillow (PIL) – Image processing

📷 Screenshots
<img width="1470" height="956" alt="Screenshot 2025-11-19 at 10 17 10 PM" src="https://github.com/user-attachments/assets/65aded48-052f-4e95-adfc-a7196eac3c37" />


🔧 Setup Instructions

Clone the repository: git clone https://github.com/yourusername/emotion-music-player.git cd emotion-music-player
Install dependencies: pip install -r requirements.txt
Set up YouTube API:
Go to Google Cloud Console
Create a project and enable the YouTube Data API v3
Generate an API key and replace it in the code: YOUTUBE_API_KEY = "YOUR_API_KEY_HERE"
Run the application: python main.py

📁 File Structure emotion-music-player/ │ ├── background2.jpg # Background image for GUI ├── main.py # Main application script ├── requirements.txt # Python dependencies └── README.md # Project documentation

✅ Requirements

Python 3.7+
Webcam and Microphone
Internet connection (for YouTube API and speech recognition)

🧪 Known Issues

Emotion detection may vary based on lighting and camera quality.
Voice recognition depends on microphone clarity and ambient noise.
Limited to one YouTube result per query.

💡 Future Enhancements

Add playlist support for each emotion.
Improve emotion classification using custom-trained models.
Integrate Spotify or other music APIs.
Add multilingual voice recognition.
Save user preferences and history.

🙌 Acknowledgments

DeepFace
Google YouTube Data API
SpeechRecognition
OpenCV
Pillow

📜 License This project is licensed under the MIT License. See the LICENSE file for details.
