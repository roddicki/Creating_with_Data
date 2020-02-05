# Part Three
In this exercise you will create a web page that plays back a video and then after 5 seconds programmatically replaces the video with another video clip selected from an array of video files.

As in the previous  section you should begin with an HTML file with a video tag,  that has an id  attribute and script tags for your JavaScript immediately before the the closing body tag.
```html
<!DOCTYPE html>
<html>
<head>
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <meta charset="UTF-8">
   <title>video</title>

</head>

<body>
   <div>Embedding a video and controlling it with javascript</div>

   <video  mute controls id="my-video">
	<source src="my-movie.mp4" type="video/mp4">
	Your browser does not support the video tag.
   </video>
	
<script> 
  //JavaScript here
</script> 
</body>

</html>
```
There are two steps to implementing this.  
1. Create some code that logs the time as the video plays back and fires a trigger after 5 seconds
2. Create some code that replaces the video playing with a new video from an array of videos

## 1.
First in the JavaScript create a variable that targets the video tag so that its properties can be accessed. Then create a function  that is triggered by the timeupdate event. 

Check it works by console logging the timeupdate
```JavaScript
let myVideo = document.querySelector("#my-video"); 
myVideo.addEventListener('timeupdate', swapVideo);

function swapVideo(){
	console.log(myVideo.currentTime);
}
```
Develop this further by logging a message when the current time is 5 seconds or more.

To prevent the the message firing at every subsequent timeupdate remove the event listener.
```JavaScript
function swapVideo(){
	console.log(myVideo.currentTime);
	if (myVideo.currentTime > 5) {
		console.log("greater than 5 secs");
		myVideo.removeEventListener('timeupdate', swapVideo);
	};
}
```
## 2.
In the final step create an array of video file names ( that need to be located in the same directory). Swap the source (src) of the video tag for the new video.
```JavaScript
let videos = ["my-movie-seagull.mp4", "my-movie-cry.mp4"];

function swapVideo(){
	console.log(myVideo.currentTime);
	if (myVideo.currentTime > 5) {
		console.log("greater than 5 secs");
		//remove the eventlistener so swapVideo isn't triggered again
		myVideo.removeEventListener('timeupdate', swapVideo);
		//set source of <video> to the first video in the array
		myVideo.src = videos[0];
		//play
		myVideo.play();
	};
}
```
# Source Code
Get the full source of this example [examples/pt3.html](examples/pt3.html)
