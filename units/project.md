

# Project Goals

- Lowest barrier of entry to Image Processing, Computer Vision and Neural Networks on the Java VM
    - by using [OpenCV](opencv.org) (and when possible [Clojure](clojuredocs.org/))
- Run Real-time models on video stream out of the box, on *your* machine OSX, Windows, Linux, ARM
- Proper Yolo (v6) Support for Real-Time Object Detection in Video Streams ![](doc/new.png) 
- Focus on easy of use for IoT devices, like the [RaspberryPi](raspberrypi.org/) or [Nvidia Jetson Nano](https://developer.nvidia.com/embedded/jetson-nano-developer-kit) 
- Native Support for Apple Silicon m1 chip ![](doc/new.png) 


# Lena in a Clojure REPL

```
(require '[opencv4.core :refer :all])

(-> "resources/lena.png"
	(imread)
	(gaussian-blur! (new-size 17 17) 9 9)
    (imwrite "resources/blurred.png"))
```

Which gives the following image transformation result:

<img src="doc/lena.png" width="25%" height="25%"></img>
<img src="doc/blurred.png" width="25%" height="25%"></img>

![](doc/new.png) 