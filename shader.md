[⬅️ Back to Portfolio](./)

# SHADER: Simple Hardware Accelerated Deferred Engine Renderer
### Interactive Graphics Final Project

<iframe
 width="100%"
 height="420"
 src="https://www.youtube-nocookie.com/embed/Cnc0-1fAuSU"
 title="SHADER Demo Recording"
 frameborder="0"
 allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
 allowfullscreen>
</iframe>

In this demo, you can see, in order of features presented:
* Spawning several hundred light sources
* Animated Lights
* Rotating Scene (important for performance comparison!)
* Deferred Textures - The textures used for computing the final image in the deferred pipeline
* The Procedural Teapot Cube
* Deferred / Forward Render Toggle

The main purpose of this demo is to showcase the performance difference between forward and deferred rendering.
Forward rendering is the process by which you draw (an expensive operation) every piece of geometry data received. Whatever you draw may very well be covered up later; you have no way of knowing what will and won't be. The GPU is smart enough to not draw data that is already "covered up" by something else that's been drawn. Say you have 10 teapots in a straight line. Worst case, you draw from back to front, drawing the backs and fronts of each teapot, only for every draw to be covered up by the next one! (Not including handles and spouts!) This means that for some pixel in the end result, you've drawn 20 different things and only kept one. That's 95% of your work wasted.

Deferred rendering waits (defers) the drawing until after the pipeline has figured out which things will be visible; i.e., what objects are in the very front of everything else. It tracks all the data necessary to compute the final draws into three textures: position, normal, and color data. In the split screen view, you can see each of those data textures in that order (left to right). The bottom-right image is the final, composited image, fully calculated from the data in those textures only - no geometry data! So we only perform the expensive draw calls when we know no work will be wasted. This takes more space in memory but is a huge increase in performance.

At the end of the demo video, if you look in the title bar of the video, you can see whether "deferred" or "forward" rendering is active. You can notice with 1,500 lights and 343 teapots that forward rendering is sluggish while deferred is still smooth. There is no change in the animation data; the cube and lights are still animated the exact same. It just takes the GPU that much more time to draw the same image per frame in forward mode.
