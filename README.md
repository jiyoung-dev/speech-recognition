# Python Speech-Recognition

## 1. Install Library 
```
pip install SpeechRecognition
pip install pyaudio
```
- SpeechRecognition: 음성을 텍스트로 변환하는 Python 라이브러리.
  - SpeechRecognition 라이브러리는 내부에 구글 Web Speech API의 API KEY가 기본으로 하드코딩 되어 들어있어 인증절차 없이 바로 사용할 수 있어 편리함.
  - 제한사항: 하루에 API 50회 호출 가능.  
- pyaudio: 마이크 기능을 위한 라이브러리. 

## 2. Audio file recognition
> 녹음된 오디오 파일을 텍스트로 출력하는 방법 
```python
import audio_file_recognition as sr

AUDIO_FILE = "(file name here)"

r = sr.Recognizer()
with sr.AudioFile(AUDIO_FILE) as source:
    audio = r.record(source) 

try:
    print("Google Speech Recognition thinks you said : " + r.recognize_google(audio, language='ko'))
except sr.UnknownValueError:
    print("Google Speech Recognition could not understand audio")
except sr.RequestError as e:
    print("Could not request results from Google Speech Recognition service; {0}".format(e))
```

## 3. Microphone speech recognition 
> 마이크 음성을 텍스트로 출력하는 방법 
```python
import speech_recognition as sr

r = sr.Recognizer()
with sr.Microphone() as source:
    print("Say something!")
    audio = r.listen(source)

try:
    print("Google Speech Recognition thinks you said : " + r.recognize_google(audio, language='ko'))
except sr.UnknownValueError:
    print("Google Speech Recognition could not understand audio")
except sr.RequestError as e:
    print("Could not request results from Google Speech Recognition service; {0}".format(e))
```

## 4. References
- [Speech recognition engine/API](https://pypi.org/project/SpeechRecognition/) <br>
- [speech_recognition](https://github.com/Uberi/speech_recognition/blob/master/examples/microphone_recognition.py)
