# Assignment Repo

Download the file from this link https://www.gyan.dev/ffmpeg/builds/
ffmpeg-release-essentials.7z

extract, rename the folder to ffmpeg
place the folder in c drive C:/

Advanced System Settings
Environment Variables
Under System Variables, search for path 
Key this "C:\ffmpeg\bin"

Exit all existing command prompts if any) and open a new command prompt.
Type "ffmpeg -version" you should see a response


Specify the full path
curl -F "file=@C:/Users/danie/Documents/Machine Learning/HTX/myrepo/common_voice/cv-valid-dev/sample-000000.mp3" http://localhost:8001/asr
E.g. {"transcription":"BE CAREFUL WITH YOUR PROGNOSTICATIONS SAID THE STRANGER","duration":"5.1"}
