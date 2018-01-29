Welcome to the Video-API-and-Pic wiki!

webRTC:(real time communication):

webcam and audio acces webRTC
https://developer.mozilla.org/en-US/docs/Web/CSS/filter
https://www.youtube.com/watch?v=6_gLU_OStK0
vidsnapper:

take photo
select filters->css filter

mozilla docs:

MediaDevices.getUserMedia()-->api
code sample

filter function:

-><filter-function> = <blur()> | <brightness()> | <contrast()> | <drop-shadow()> | <grayscale()> | <hue-rotate()> | <invert()> | <opacity()> | <saturate()> | <sepia()>

//get media stream


const video=document.getElementById('video');
	
navigator.mediaDevices.getUserMedia({ video : true, audio : false }
)
 .then(function(stream){  // stream
   // link to video source
  video.srcObject = stream;
  video.play();
 })
 .catch(function(err) { 
  console.log(' Error: ${err}');
});

  // play when ready
  video.addEventListener('canplay',function(e){
 if(!streaming)
 { 
  // set video /canves  height
  height = video.videoHeight / ( video.videoWidth / width);
  video.setAttribute('width','width');
  video.setAttribute('height','height');
  canvas.setAttribute('width','width');
  canvas.setAttribute('height','height');

   streaming = true;
} 
} , false);

// take photo add event listener

  photoButton.addEventListener('click',function(e){
  takePicture();
   e.preventDefault();
  },false);
 
 /// fiter event
  photoFilter.addEventListener('change',function(){
  // set filter to chosen option
   filter = e.target.value;
   // set filter to video
   video.style.filer=filter;
   e.preventDefault();
   });

  //clear event
  clearButton.addEventListener('click',function(e){
  // clear photos
   photos.innerHTML='';
  //changes filter back to none
   filter = 'none';
   // set video filter
   video.style.filter=filter;
 // reset elect list
 photoFilter.selectedIndex = 0;
   
})


  
   function takePicture(){
   /// create canvas
    cost context = canvas.getContext('2d');
    if( width && height){
     canvas.width= width;
     canvas.height= height;
   //draw an image of the video on the canvas 
   context.drawImage(video,0,0,width,height);

  //create image from the canvas  
   const imgurl = canvas.toDataURL('image/png');

  // set img src
  img.setAttribute('src',imgUrl); 

 // set image filter
 img.style.filter = filter;

  // add image to photos

 photos.appendChild(img);
   
  console.log(imgUrl);
  }
   }


