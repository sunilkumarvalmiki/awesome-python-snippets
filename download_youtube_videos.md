
- [pytube3](#pytube): [https://pypi.org/project/pytube3/](https://pypi.org/project/pytube3/)
- [pafy](#pafy): [https://pypi.org/project/pafy/](https://pypi.org/project/pafy/)


## PYTUBE 
- Install Pytube Library :
```py
pip install pytube3
```

```py

#importing the module 
from pytube import YouTube

try:
    #link of the video to be downloaded 
    yt = YouTube('https://www.youtube.com/watch?v=HRmdj-HpJyE&ab_channel=TraversyMedia')
except:
    print("given url is not valid")

#to get the name of the file 
print("title : " + yt.title)

# to get thumbnail url
print("thumbnail : " + yt.thumbnail_url)

try:
    #get the video with the resolution passed in the get('137') function, 137-1080.
    stream = yt.streams.get_by_itag('137')
except:
    print("Given itag is not present, Please change the itag")

try: 
    #Downloading to the below location
    stream.download('S:\youtube')
    # success message
    print('Video Downloaded . . . .')
except:
    # error mesage 
	print("error in given location or internet ! ") 

```
---

## PAFY
- Install pafy Library :
```py
pip install pafy
```
- Install youtube-dl Library :
```py
pip install youtube-dl
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
stream = video.getbest() 

#print(best.resolution, best.extension) 

try:
    # Download the video 
    stream.download(filepath="S:\youtube")
    # success message
    print("Video Downloaded")
except:
    # erroe message
    print("error while downloading . . . .") 

```