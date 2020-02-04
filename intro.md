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
Make sure that the relative path to your video file is correct
```html
<video id="my-video">
  <source src="path/to/my-movie.mp4" type="video/mp4">
  Your browser does not support HTML5 video.
</video>
```
Experiment adding the controls,  loop and autoplay attributes to see the effect that they have. 
```html
<video id="my-video" controls loop autoplay>
  <source src="path/to/my-movie.mp4" type="video/mp4">
  Your browser does not support HTML5 video.
</video>
```
Now you will add some HTML links / buttons and JavaScript to play and pause the video. Add  HTML buttons underneath the video tag and and add a script tag immediately before the the bottom of the body tag (in a production environment it would be better to link a separate JavaScript file, but for this simple prototype script tags embedded in the HTML will suffice).
```html
  <video  mute controls id="my-video">
    <source src="my-movie.mp4" type="video/mp4">
    Your browser does not support the video tag.
  </video>

  <div>
    <a href="#" id="play-video">Play</a>
    <a href="#" id="pause-video">Pause</a>
  </div>
  <script> 
    //js goes here
  </script> 
</body>
```
Now  target JavaScript to to target the video tag so that it's play and pause properties can be accessed.
```JavaScript
  let myVideo = document.querySelector("#my-video"); 
```
Also target the play and pause links / buttons and add an event listener to listen for a click event on either link / button. 
```JavaScript
  let playBtn = document.querySelector("#play-video"); 
  playBtn.addEventListener("click", play);

  let pauseBtn = document.querySelector("#pause-video"); 
  pauseBtn.addEventListener("click", pause); 
```
Now create the play and pause functions the the event listeners will trigger when they detect a click. these functions use the play() and pause() method that is built into to the API for the HTML video tag.
```JavaScript
  function play() { 
      myVideo.play(); 
  }

  function pause() { 
      myVideo.pause(); 
  }  
```
