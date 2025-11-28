import cv2
import time
import webbrowser
from deepface import DeepFace
from googleapiclient.discovery import build
import speech_recognition as sr

# Step 5: Capture verbal prompt
def capture_verbal_prompt():
    recognizer = sr.Recognizer()
    mic = sr.Microphone()
    print("Say the mood or emotion you want...")
    with mic as source:
        recognizer.adjust_for_ambient_noise(source)
        audio = recognizer.listen(source)
    try:
        text = recognizer.recognize_google(audio)
        print(f"You said: {text}")
        return text.lower()
    except sr.UnknownValueError:
        print("Sorry, I couldn't understand.")
        return None
    except sr.RequestError:
        print("Speech recognition service error.")
        return None

# Step 1: Capture image from webcam
def capture_image(filename="captured_face.jpg"):
    cap = cv2.VideoCapture(0)
    print("Capturing image... Look at the camera.")
    time.sleep(2)
    ret, frame = cap.read()
    if ret:
        cv2.imwrite(filename, frame)
        print("Image captured.")
        cap.release()
        return True
    else:
        print("Failed to capture image.")
        cap.release()
        return False

# Step 2: Detect emotion using DeepFace
def detect_emotion(image_path="captured_face.jpg"):
    print("Analyzing emotion...")
    result = DeepFace.analyze(img_path=image_path, actions=['emotion'], enforce_detection=False)
    emotion = result[0]['dominant_emotion']
    print(f"Detected Emotion: {emotion}")
    return emotion

# Step 3: Map emotion to music mood
def map_emotion_to_keywords(emotion):
    emotion_to_keywords = {
        "happy": "happy upbeat music",
        "sad": "sad emotional acoustic songs",
        "angry": "angry rock metal music",
        "surprise": "surprising energetic music",
        "neutral": "chill ambient music",
        "fear": "calming instrumental music",
        "disgust": "grunge alternative music"
    }
    return emotion_to_keywords.get(emotion.lower(), "mood music")

# Step 4: Search YouTube for music
def search_youtube_music(query, api_key):
    print(f"Searching YouTube for: {query}")
    youtube = build("youtube", "v3", developerKey=api_key)
    request = youtube.search().list(
        part="snippet",
        q=query,
        type="video",
        videoCategoryId="10",  # Music category
        maxResults=1
    )
    response = request.execute()
    if response["items"]:
        video_id = response["items"][0]["id"]["videoId"]
        video_url = f"https://music.youtube.com/watch?v={video_id}"
        print(f"Opening: {video_url}")
        webbrowser.open(video_url)
    else:
        print("No music found for this emotion.")

# Main function
def main():
    if capture_image():
        emotion = detect_emotion()
        query = map_emotion_to_keywords(emotion)
        YOUTUBE_API_KEY = "AIzaSyCjOxopnMpVIp-XQuY1H0paaCwRVQzkvic"  # Replace with your actual API key
        search_youtube_music(query, YOUTUBE_API_KEY)
    else:
        print("Skipping emotion analysis due to failed image capture.")
def main():
    choice = input("Type 'voice' for verbal prompt or 'face' for emotion detection: ").strip().lower()
    
    if choice == "voice":
        spoken_emotion = capture_verbal_prompt()
        if spoken_emotion:
            query = map_emotion_to_keywords(spoken_emotion)
            YOUTUBE_API_KEY = "AIzaSyCjOxopnMpVIp-XQuY1H0paaCwRVQzkvic"
            search_youtube_music(query, YOUTUBE_API_KEY)
        else:
            print("No valid verbal input detected.")
    
    elif choice == "face":
        if capture_image():
            emotion = detect_emotion()
            query = map_emotion_to_keywords(emotion)
            YOUTUBE_API_KEY = "AIzaSyCjOxopnMpVIp-XQuY1H0paaCwRVQzkvic"
            search_youtube_music(query, YOUTUBE_API_KEY)
        else:
            print("Skipping emotion analysis due to failed image capture.")
    else:
        print("Invalid choice. Please type 'voice' or 'face'.")

if __name__ == "__main__":
    main()
