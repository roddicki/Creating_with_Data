# Creating with Data - HTML 5 Video
It is quite straightforward to manipulate video in a webpage using JavaScript.

This workshop will explore the base code needed to to play, pause, swap videos.

There are two main references online that also explore this:

Simpler
https://www.w3schools.com/tags/ref_av_dom.asp 

More complex 
https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Client-side_web_APIs/Video_and_audio_APIs 

The first part of this workshop you will create a play / pause button, a restart button and a timer.

The second part of the  workshop you will load a video from an array of video files at a set time during play back.

# Part One
Start with an  HTML document that embeds an MP4 video using the video tag.
```html
<video id="myVideo" width="320" height="176">
  <source src="mov_bbb.mp4" type="video/mp4">
  Your browser does not support HTML5 video.
</video>
```
