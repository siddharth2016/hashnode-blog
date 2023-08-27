---
title: "Download YouTube Videos Using Python - Your Own YouTube Downloader"
seoTitle: "Download YouTube Videos Using Python - Your Own YouTube Downloader"
seoDescription: "In this article, we are going to see how to download any youtube video using python and pytube in under 10 lines of code."
datePublished: Thu Apr 29 2021 13:26:45 GMT+0000 (Coordinated Universal Time)
cuid: cko2x8bh701w4des110xc7fp9
slug: download-youtube-videos-using-python-your-own-youtube-downloader
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1619702191990/tw7mwb4BJ.png
tags: python, opensource, learning, beginners, youtube

---

Do you find it troublesome to always look for a YouTube video downloader with your privacy at risk? Downloading a YouTube video using an external extension might be maddening because of the mouse click ads and other issues while using that extension.

So, why not we create our own bot that can download any YouTube video with just simply running a Python script? Everything would be in our control then, awesome, right?

In this article, we are going to see how we can make a Python script to automate the YouTube video downloading activity.

After going through this article, you can say `NO` to all those annoying ads, privacy issues, authorisation to different extensions and can finally have total control.

Let's get started!

---

### What Are We Going To Use?

We are going to use Python and one of its amazing 3rd party library, [pytube](https://pypi.org/project/pytube/).

To install pytube:

```bash
$ pip install pytube
Collecting pytube
  Downloading pytube-10.7.2-py3-none-any.whl (42 kB)
     |████████████████████████████████| 42 kB 3.4 MB/s 
Installing collected packages: pytube
Successfully installed pytube-10.7.2
$
```

More on pytube:

- pytube is a very serious, lightweight, dependency-free Python library (and command-line utility) for downloading YouTube Videos.
- pytube is a lightweight library written in Python. It has no third-party dependencies and aims to be highly reliable.
- pytube also makes pipelining easy, allowing you to specify callback functions for different download events, such as `on progress` or `on complete`.
- Finally, pytube also includes a command-line utility, allowing you to quickly download videos right from the terminal.

Features:

- Support for both progressive & DASH streams.
- Support for downloading complete playlist.
- Easily register `on_download_progress` & `on_download_complete` callbacks.
- Command-line interfaced included.
- Caption track support.
- Outputs caption tracks to `.srt` format (SubRip Subtitle).
- Ability to capture thumbnail URL.
- Extensively documented source code.
- No third-party dependencies (written in pure Python).

On a high level, to download a video using the library in a script, we'll need to first import the YouTube class from the library, and pass it an argument of the video URL. Then we can download different streams present on that YouTube object.

Now, let's move on to use this information to build our first YouTube video downloader.

### Get The Streams

First, we will make a simple script to get all the available streams for the given YouTube video URL. Open a file name it whatever you like with the `.py` extension, let's say for our case we name it `pytube_demo.py`, add the following code in it and run:

```python
# ./pytube_demo.py

from pytube import YouTube

video_url = input("Enter YouTube Video URL: ")
youtube_obj = YouTube(video_url)
print(youtube_obj.streams)
```

After you hit run, when the terminal prompts you to enter a video URL, enter this `https://www.youtube.com/watch?v=fibIyvTleqc`, it is one of my favourite songs `Daydreamer` by `AURORA`.

> *Note: You can enter any YouTube video URL here, what we are going to explore further doesn't depend on which URL you enter.*

```bash
Enter YouTube Video URL: https://www.youtube.com/watch?v=fibIyvTleqc
[<Stream: itag="18" mime_type="video/mp4" res="360p" fps="25fps" vcodec="avc1.42001E" acodec="mp4a.40.2" progressive="True" type="video">, <Stream: itag="137" mime_type="video/mp4" res="1080p" fps="25fps" vcodec="avc1.640028" progressive="False" type="video">, <Stream: itag="248" mime_type="video/webm" res="1080p" fps="25fps" vcodec="vp9" progressive="False" type="video">, <Stream: itag="136" mime_type="video/mp4" res="720p" fps="25fps" vcodec="avc1.4d401f" progressive="False" type="video">, <Stream: itag="247" mime_type="video/webm" res="720p" fps="25fps" vcodec="vp9" progressive="False" type="video">, <Stream: itag="135" mime_type="video/mp4" res="480p" fps="25fps" vcodec="avc1.4d401e" progressive="False" type="video">, <Stream: itag="244" mime_type="video/webm" res="480p" fps="25fps" vcodec="vp9" progressive="False" type="video">, <Stream: itag="134" mime_type="video/mp4" res="360p" fps="25fps" vcodec="avc1.4d401e" progressive="False" type="video">, <Stream: itag="243" mime_type="video/webm" res="360p" fps="25fps" vcodec="vp9" progressive="False" type="video">, <Stream: itag="133" mime_type="video/mp4" res="240p" fps="25fps" vcodec="avc1.4d4015" progressive="False" type="video">, <Stream: itag="242" mime_type="video/webm" res="240p" fps="25fps" vcodec="vp9" progressive="False" type="video">, <Stream: itag="160" mime_type="video/mp4" res="144p" fps="25fps" vcodec="avc1.4d400c" progressive="False" type="video">, <Stream: itag="278" mime_type="video/webm" res="144p" fps="25fps" vcodec="vp9" progressive="False" type="video">, <Stream: itag="140" mime_type="audio/mp4" abr="128kbps" acodec="mp4a.40.2" progressive="False" type="audio">, <Stream: itag="249" mime_type="audio/webm" abr="50kbps" acodec="opus" progressive="False" type="audio">, <Stream: itag="250" mime_type="audio/webm" abr="70kbps" acodec="opus" progressive="False" type="audio">, <Stream: itag="251" mime_type="audio/webm" abr="160kbps" acodec="opus" progressive="False" type="audio">]
```

So, we got a list of `Stream` objects, each stream object giving us information about different aspects of a video.

If we see `res` attribute of stream object, we see that we have `360p`, `1080p`, `720p`, `480p`, `240p` and `144p` with different `vcodec` attribute. This `res` represents the resolution of a video, we can select any stream of desired resolution to download.

Also, notice that we have only audio option streams available as well to download.

Next, we will create a filter for video resolution and to keep it simple we will not dive into audio downloadable streams.

### Filter Stream Based On Resolution

Update the code in the `pytube_demo.py` file to the below code:

```python
# ./pytube_demo.py

from pytube import YouTube

def get_stream_for_res(streams, res):
    """
    Filter on the basis of a given resolution. Return a list of filtered streams.
    """
    stream = list(filter(lambda x: x.resolution == res, streams))
    return stream

video_url = input("Enter YouTube Video URL: ").strip()
youtube_obj = YouTube(video_url)

video_res = input(f"Enter YouTube Video Resolution for {youtube_obj.title}: ").strip()
req_stream_obj = get_stream_for_res(youtube_obj.streams, video_res)
print(req_stream_obj)
```

Hit run and we can see following output in the terminal:

```bash
Enter YouTube Video URL: https://www.youtube.com/watch?v=fibIyvTleqc
Enter YouTube Video Resolution for AURORA - Daydreamer (Audio): 720p
[<Stream: itag="136" mime_type="video/mp4" res="720p" fps="25fps" vcodec="avc1.4d401f" progressive="False" type="video">, <Stream: itag="247" mime_type="video/webm" res="720p" fps="25fps" vcodec="vp9" progressive="False" type="video">]
```

First, we take the video URL and creates the `YouTube` object, then we take custom input from the user while displaying the title of the video using `youtube_obj.title`. After receiving the resolution, say `720p`, we call the function `get_stream_for_res` that filters the given list of streams on the given resolution. At last, we can see the output, it contains 2 stream objects in a list, both objects have different values for some attributes but have the same resolution.

Without diving deep on what all other attribute means, let's just simply take the first element of the list and download the video.

### Download Stream Based On Resolution

Now update the code to the following to download the YouTube video (complete script):

```python
# ./pytube_demo.py

from pytube import YouTube

def get_stream_for_res(streams, res):
    stream = list(filter(lambda x: x.resolution == res, streams))
    return stream

video_url = input("Enter YouTube Video URL: ").strip()
youtube_obj = YouTube(video_url)

video_res = input(f"Enter YouTube Video Resolution for {youtube_obj.title}: ").strip()
req_stream_obj = get_stream_for_res(youtube_obj.streams, video_res)[0]

req_stream_obj.download()
print(f"YouTube Video {youtube_obj.title} Downloaded With Resolution {video_res}")
```

When we run the above script, we get the following output and a downloaded video:

```bash
Enter YouTube Video URL: https://www.youtube.com/watch?v=fibIyvTleqc
Enter YouTube Video Resolution for AURORA - Daydreamer (Audio): 720p
YouTube Video AURORA - Daydreamer (Audio) Downloaded With Resolution 720p
```

Now, if we check our directory where we ran the script, we can find the downloaded video.

**Note:**

> You may notice that some streams listed have both a video codec and audio codec, while others have just video or just audio, this is a result of YouTube supporting a streaming technique called Dynamic Adaptive Streaming over HTTP (DASH).

> In the context of pytube, the implications are for the highest quality streams; you now need to download both the audio and video tracks and then post-process them with software like FFmpeg to merge them.

> The legacy streams that contain the audio and video in a single file (referred to as “progressive download”) are still available, but only for resolutions 720p and below.

The video downloaded from the given code has a Stream object whose attribute `progressive` is `False`. The given video URL does not have legacy streams available for `720p` but if you notice there is one stream with `progressive` as `True` and `res` as `360p`.

```bash
<Stream: itag="18" mime_type="video/mp4" res="360p" fps="25fps" vcodec="avc1.42001E" acodec="mp4a.40.2" progressive="True" type="video">
```

So, go ahead and experiment with it and don't forget to check out the `progressive` attribute.

### What Next?

Well, that's it from me. If you followed this and ran the final script, you would be seeing a downloaded video in your working directory.

You can take it to the next level by creating a UI for this utility. You can host this as a service that would be strictly private to you.

What are you waiting for then? Use Tkinter, PyQT, Kivy, Flask or Django and make a UI with more functions like a select option for audio and video, for video resolution and for audio ABR, etc. and say `NO` to all those annoying ads, privacy issues, several authorisations to different extensions and have total control over your downloaded videos.

---

- Just starting your Open Source Journey? Don't forget to check [Hello Open Source](https://github.com/siddharth2016/hello-open-source)

- Want to showcase your Python project or just out there to explore? Check [Awesome Python Repos](https://github.com/siddharth2016/awesome-python-repos)

- Want to make a simple and awesome game from scratch? Check out [PongPong](https://github.com/siddharth2016/PongPong)

- Want to `++` your GitHub Profile README? Check out [Quote - README](https://github.com/marketplace/actions/quote-readme)

Till next time!

Namaste 🙏