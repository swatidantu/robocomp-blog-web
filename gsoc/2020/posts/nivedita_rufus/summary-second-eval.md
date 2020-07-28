## A Summary of my Contributions in the Second phase of GSoC 2020  

28 July 2020

My first phase of the GSoC Journey ended with an implementation of the the people Counter from a single view which involved a lot literature survey and some unprecedented problems which required some brainstorming solutions. This made my work for the second phase much less hectic and simpler as I had to find the best way to integrate the information given by each image from multiple cameras. I have proposed and implemented two aproaches for different type of views as I had promised in my proposal.  
The first one being, the addition of a preprocessing step of of image stitching for partially overlapping views. This step involves stitching of the images together to form a single image which is then passed into the counting module. This results in a performance overhead which can be compesated by adjusting the `skip_frames` parameter.  
An example of this preprocessing step is shown below:  
![](images/image1.jpg)
![](images/image2.jpg)  
The image obtained by stitching is shown below:  
![](images/stitched.jpg)  
Unlike many image stitching algorithms that are sensitive to the order of input images, this method is not only insensitive to the order of the input images but also orientation and illumination changes. I also verified this by introducing some random illumination changes(dark, bright, hazy) [here](https://github.com/niveditarufus/ImageStitching).
An example is hown below:  
![](images/stitchedVideo.gif)  