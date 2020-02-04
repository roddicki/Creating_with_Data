# Part Three
In next workshop you will load a video from an array of video files at a set time.

As in the previous  section you should begin with a HTML file with a video tag,  that has an id  attribute and script tags for your JavaScript immediately before the the closing body tag.
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
There are two steps to implementing this.  First in the JavaScript create a variable that targets the video tag so that its properties can be accessed. Then create a function  that is triggered by the timeupdate event. 

Check it works by console logging the timeupdate
```JavaScript
<script> 
	let myVideo = document.querySelector("#my-video"); 
	myVideo.addEventListener('timeupdate', swapVideo);

	function swapVideo(){
		console.log(myVideo.currentTime);
	}

</script> 
```
