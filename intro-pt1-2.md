# Creating with Data - HTML 5 Video
It is quite straightforward to manipulate video in a webpage using JavaScript.

This workshop will explore the base code needed to to play, pause, swap videos.

There are two main references online that also explore this:

Simpler
https://www.w3schools.com/tags/ref_av_dom.asp 

More complex 
https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Client-side_web_APIs/Video_and_audio_APIs 

The first part of this workshop you will create a play / pause button, and a restart button 

In the second part you will add a timer.

The third part of the  workshop you will load a video from an array of video files at a set time during play back.

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
  playBtn.addEventListener("click", playVideo);

  let pauseBtn = document.querySelector("#pause-video"); 
  pauseBtn.addEventListener("click", pauseVideo);
```
Now create the playVideo and pauseVideo functions the the event listeners will trigger when they detect a click. these functions use the play() and pause() method that is built into to the API for the HTML video tag.
```JavaScript
  function playVideo() { 
      myVideo.play(); 
  }

  function pauseVideo() { 
      myVideo.pause(); 
  } 
```
Once you have  successfully tested this consider changing the play and pause button to a single play / pause using the the paused property of the HTML video.

Change your playVideo() function so that it uses an if statement as follows
```JavaScript
  function playVideo() { 
    if (myVideo.paused) {
      myVideo.play(); 
    }
    else {
      myVideo.pause();
    };
  }
```
Now we will add a restart button that sets the player back to the beginning of the video clip.

To do this we need to add another link / button.
```html
  <div>
    <a href="#" id="play-video">Play</a>
    <a href="#" id="pause-video">Pause</a>
    <a href="#" id="restart-video">Pause</a>
  </div>
```
And an event listener to listen for a click that will trigger a restart function.
```JavaScript
  let restartBtn = document.querySelector("#restart-video");
  restartBtn.addEventListener("click", restartVideo); 
```
Then finally add the restart function using the currentTime property of the HTML video element. The function simply sets the current time to 0s. 
```JavaScript
  function restartVideo(){
    myVideo.currentTime = 0;
  }
```

# Part Two
In this next section continue with the same HTML page and JavaScript and add a timer to the web page. 
The timer will display how many seconds have elapsed since the start of the video.

The timer will use the timeupdate Property of the HTML video. Each  moment the video  advances  the timeupdate event fires and returns the current time of the video.

To implement this In the HTML add a new div tag with an id.
```html
  <div id="current-time">0</div>
```
 In the JavaScript  add a timeupdate event listener that triggers a function called displayTime() every time it fires.
```JavaScript
  myVideo.addEventListener('timeupdate', displayTime);
```
Add the function displayTime(), so that the inner HTML of the current-time div updates
```JavaScript
  function displayTime(){
    document.querySelector("#current-time").innerHTML = myVideo.currentTime;
  }
```
When you test this page you should see the video time up date as the video plays back.
# Source Code
The full source code is available at
[examples/pt1-2.html](examples/pt1-2.html)

## Continue
Once you have completed this move on to Part 3 [intro-pt3.md](intro-pt3.md)
