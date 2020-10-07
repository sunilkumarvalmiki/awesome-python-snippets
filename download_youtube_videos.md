
- [pytube](#pytube): [https://pypi.org/project/pytube/](https://pypi.org/project/pytube/)
- [pafy](#pafy): [https://pypi.org/project/pafy/](https://pypi.org/project/pafy/)


## PYTUBE 
- Install Pytube Library :
```py
pip install pytube
```

```py
#importing the module 
from pytube import YouTube 

#Locatn to save the downloaded video
SAVE_PATH = "S:\youtube" 

#link of the video to be downloaded 
link="https://www.youtube.com/watch?v=HRmdj-HpJyE&ab_channel=TraversyMedia"

try: 
	#object creation using YouTube which was imported in the beginning 
	yt = YouTube(link) 
except: 
	print("Connection Error") #to handle exception 

#filters out all the files with "mp4" extension 
mp4files = yt.filter('mp4') 

#to set the name of the file 
yt.set_filename('React-Admin-Crash-Course Video')

#get the video with the extension and resolution passed in the get() function 
d_video = yt.get(mp4files[-1].extension,mp4files[-1].resolution) 
try: 
	#downloading the video 
	d_video.download(SAVE_PATH) 
except: 
	print("Some Error ! ") 
print('Video Downloaded . . . .') 
```
---

## PAFY
- Install pafy Library :
```py
pip install pafy
```

```py
import pafy 

#link of the video to be downloaded
url = "https://www.youtube.com/watch?v=EeoyxbpQ2K4&ab_channel=edureka%21"
video = pafy.new(url) 

streams = video.streams 
for i in streams: 
	print(i) 
	
# get best resolution regardless of format 
best = video.getbest() 

print(best.resolution, best.extension) 

# Download the video 
best.download() 
```