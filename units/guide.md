


# Support for OpenCV 4.7.0 is in!

Origami is a generated opencv wrapper for Clojure, which allows opencv code to be written in a concise way, by putting emphasis on processing pipelines.


```
(require
  '[opencv4.utils :as u]
  '[opencv4.core :refer :all])

(->
 (imread "doc/cat_in_bowl.jpeg")
 (cvt-color! COLOR_RGB2GRAY)
 (canny! 300.0 100.0 3 true)
 (bitwise-not!)
 (u/resize-by 0.5)
 (imwrite "doc/canny-cat.jpg"))
```

<img src="doc/cat_in_bowl.jpeg" width="50%" height="50%"/>

<img src="doc/canny-cat.jpg" width="50%" height="50%"/>

# Origami ecosystem

<img src="doc/origami-layout.svg"/>

# Books on using Origami

[Java Image Processing Recipes: With OpenCV and JVM](http://a.co/3iImWz7) published by Apress will show you all the tricks to play and produce art and understand the underlying concepts of origami.

<img src="doc/book.jpg" width="25%" height="25%"/>


[Real-Time IoT Imaging with Deep Neural Networks: Using Java on the Raspberry Pi 4 ](https://www.amazon.com/Real-Time-Imaging-Deep-Neural-Networks/dp/1484257219/ref=sr_1_1)

<img src="doc/book2.jpg" width="25%" height="25%"/>

# Getting Started 

## Required Software to install

If you do not have one, [download](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) and install a Java Development Kit.

Even better, we recommend using [sdkman](https://sdkman.io/):

```
sdk install java 8.0.242-zulu
```

Origami is [tested](https://travis-ci.org/hellonico/origami) on most major Java Virtual Machines for compatibility.

## 2 minutes intro: using clj

If you already have the clojure CLI, clj, installed then you can be ready in 2 minutes.

In a new folder, create the deps.edn file:

```
{:mvn/repos
   {"vendredi" {:url "https://repository.hellonico.info/repository/hellonico/"}}
 :deps 
   { origami {:mvn/version "4.7.0-0"}}}
```

Start a repl:

```
clj 
```

Require the two most used origami namespaces:

```
   (require
    '[opencv4.utils :as u]
    '[opencv4.core :refer :all])
```

Finally, here is a short snippet to download an image from a url, resize it and store it to the local file system.

```
(-> "https://raw.githubusercontent.com/hellonico/origami/master/doc/cat_in_bowl.jpeg"
    (u/mat-from-url)
    (u/resize-by 0.3)
    (u/imshow "cat.jpg"))
```

You'll get a cat in your own bowl:

<img src="doc/cat_in_bowl.jpeg" width="30%" height="30%"/>

You also would know you can also directly load, turn to gray, and change the size with:

```
(-> "https://raw.githubusercontent.com/hellonico/origami/master/doc/cat_in_bowl.jpeg"
    (u/mat-from-url IMREAD_REDUCED_GRAYSCALE_4)
    (imwrite "cat.jpg"))
```

<img src="doc/cat_in_bowl_bw.jpeg"  width="25%" height="25%"/>


Or if you want to show it in a frame instead of writing to a file:

```
(-> "https://raw.githubusercontent.com/hellonico/origami/master/doc/cat_in_bowl.jpeg"
    (u/mat-from-url IMREAD_REDUCED_GRAYSCALE_4)
    (u/imshow))
```


## Scripting with inlein

This is one of the best way to do computer vision scripting. You can install [inlein](http://inlein.org/) which will handle the clojure scripting for you. 

Parameters for memory and dependencies are added at the top of the file, and the code itself is inline within the script. 

```clojure
#!/usr/bin/env inlein
'{:jvm-opts ["-XX:+TieredCompilation" "-XX:TieredStopAtLevel=1" "-Xverify:none"]
  :dependencies [[org.clojure/clojure "1.10.0"][origami "4.7.0-0"]]}

(require '[opencv4.core :refer [VERSION]]) 
(println "Using OpenCV Version: " VERSION "...")
```

This is very useful for IoT/Raspberry testing.

For example, the below starts a video stream with some real-time transformation.

```
#!/usr/bin/env inlein

'{:dependencies [[org.clojure/clojure "1.10.0"][origami/origami "4.7.0-0"]]}

(ns opencv4.webcam
  (:require
    [opencv4.core :refer :all]
    [opencv4.utils :as u]))

 (u/simple-cam-window 
   (fn [buffer]
   (u/resize-by buffer 0.4)
   (let [ output (new-mat) bottom (-> buffer clone (flip! -1)) ]
    (-> buffer (cvt-color! COLOR_RGB2GRAY) (cvt-color! COLOR_GRAY2RGB))
    (put-text buffer (str (java.util.Date.)) (new-point 10 50) FONT_HERSHEY_PLAIN 1 (new-scalar 255 255 0) 1)
    (vconcat [buffer bottom] output)
    output)))
```

In the same way, the below performs Object Detection using Yolo Tiny on a video stream.

```
#!/usr/bin/env inlein
'{:dependencies [[org.clojure/clojure "1.10.0"][origami-dnn "0.1.13"]]}

(ns demo.yolo.cam
  (:require   [origami-dnn.net.yolo :as yolo]
                     [origami-dnn.draw :as d]
                     [opencv4.dnn.core :as origami-dnn]
                     [opencv4.utils :as u]))

   (let [[net _ labels] 
     (origami-dnn/read-net-from-repo "networks.yolo:yolov3-tiny:1.0.0")]
			  (u/simple-cam-window
			  {:frame {:fps true}}
			   (fn [buffer]
			     (-> buffer 
						     (yolo/find-objects net) 
						     (d/blue-boxes! labels) ))))
```

## Using Leiningen, working in Clojure

Create a brand new origami based project using the [clj-opencv](https://github.com/hellonico/clj-opencv) Leiningen project template

```
# install the sample
lein new clj-opencv hello-origami

# change directory
cd hello-origami

# run the template simple example
lein run

# or using clj 
clj -m opencv4.ok
# 
clj -m opencv4.lena
```

Some examples are included in the project template.
Origami Setup Check (including OpenCV native dependencies check)

```
lein run -m opencv4.ok
```

Some Simple OpenCV transformation using origami

```
lein run -m opencv4.simple
```

A more advanced set of imaging transformation.

```
lein run -m opencv4.tutorial
```

Webcam Sample

```
lein run -m opencv4.videosample
```

## Using Leiningen, working in Java

```
# install the sample
lein new jvm-opencv java-origami

cd java-origami
lein run 
```


## Jupyter Notebook

The lein-jupyter plugin is added to the project.clj, so if you have followed the installation steps for lein-jupyter, you should have an integrated working jupyter notebook.
```
lein jupyter notebook
```

![](doc/jupyter.png)



## Gorilla Based Notebook

> This is about to be deprecated in favor of jupyter notebooks ...

The gorilla plugin is included in the project template. 

```
lein notebook

# or without samples and just the docker image
docker run -it -p10000:10000 hellonico/origami lein notebook
```
Two notebooks are included in the project template:

- [http://0.0.0.0:10000/worksheet.html?filename=notes/practice.clj](http://0.0.0.0:10000/worksheet.html?filename=notes/practice.clj)
- [http://0.0.0.0:10000/worksheet.html?filename=notes/empty.clj](http://0.0.0.0:10000/worksheet.html?filename=notes/empty.clj)


## origami-starter-clojure

A copy of the samples can also be cloned from a generated project.

```
git clone https://github.com/hellonico/origami_samples.git
```

## origami-starter-java project

Checkout this repository and get started in Java straight away.

```
git clone https://github.com/hellonico/opencv-java-template.git
```


## Docker official image

```
# default run with lein
docker run -it hellonico/origami lein run

# official image and custom src folder using clj
docker run -it -v <path_to_local_src>:/usr/src/app/src  hellonico/origami clojure -m <your_custom_namespace>

# start the gorilla notebook
docker run -it -p10000:10000 hellonico/origami lein notebook

# with the official image and clj
docker run -it hellonico/origami clojure -m opencv4.ok
docker run -it hellonico/origami clojure -m opencv4.simple

# official image and custom src folder
docker run -it -v <path_to_local_src>:/usr/src/app/src hellonico/origami clj -m <your_custom_namespace>
```

## Using sbt and scala

```
mkdir scallop
cd scallop
sbt new hellonico/origami-starter-scala.g8
```

```
# Show List of Main Target in the templates
sbt 'show discoveredMainClasses' 
```

```
# Display an OpenCV Mat 
sbt 'runMain JustMat'
# Apply Canny Fiter on an Image
sbt 'runMain CannyFast <image_url>'
# Run a webcam with a cartoon filter
sbt 'runMain CartoonCam'
```

## electron based IDE

An experimental self-contained native application for windows and osx can be downloaded from the following project:

https://github.com/hellonico/origami-electron/releases

<img src="doc/electron-osx.png" width="50%" height="50%"/>

<img src="doc/electron-windows.png" width="50%" height="50%"/>



## Running on AWS with Amazon Lambdas

The [origami-aws-lambdas](https://github.com/hellonico/origami-aws-lambdas) has everything included to get you started deploying your lambdas.

Basically, writer a handler as shown below:

```clojure
(ns lando.origami
    (:require [opencv4.core :refer :all])
    (:gen-class
      :methods [^:static [handler [String] String]]))

(defn -handler [s]
   (str "Using OpenCV Version: " VERSION ".."))
```

## Create super fast native binaries using Bazel

See how the build tool [Bazel](https://bazel.build/) can help you creating binaries based on standard Origami code.

```
git clone git@github.com:hellonico/origami-bazel.git
```

Build the main application by running:

```
$ bazel build :origami-check
```

Test the code by running:

```
$ bazel test :tests
```

Finally, run the application by running

```
$ ./bazel-bin/origami-check
```

### Compare speed


here we compare the speed of ok.clj executed with inlein
```
$ time ./ok.clj 
Loaded:opencv_java420
Using OpenCV Version:  4.2.0 ...

real	0m3.093s
user	0m2.326s
sys	0m0.552s
```

And, almost the same code executed via a bazel created binary:
```
time ./bazel-bin/origami-check
Loaded:opencv_java420
[  1,   0,   0;
   0,   1,   0;
   0,   0,   1]

real	0m0.786s
user	0m0.618s
sys	0m0.256s
```

> Note that the speed of the image processing is unaffected, only the start speed of the program is.
>

### Other bazel based demo applications

- *origami-check*: load and display an opencv mat
- *origami-webcam*: run the webcam
- *origami-greycam*: run the webcam with an extra origami filter to turn the stream to grey 
- *origami-cartooncam*: run the webcam with an extra origami filter to cartoonify the stream
- *origami-yolocam*: run the webcam with yolo detection

# Samples

## in clojure ...

For many, many more examples, you can also clone and check the [https://github.com/hellonico/opencv-fun](opencv-fun) repository:

```
git clone https://github.com/hellonico/opencv-fun.git
```

## in java ...

```
git clone https://github.com/hellonico/opencv4_java_tutorial.git
```

## in kotlin ...

*Use the java_tutorial project for now.*

## in scala ...

*Use the scala template for now.*

## in android ...

*Use the Android Starter Template for now.*

## with javacv ...

There is a starter project showing basic computer vision steps using [javacv](https://github.com/bytedeco/javacv) compiled binaries.

```bash
git clone https://github.com/hellonico/origami-javacv.git
```

### Using Leiningen, the following examples/aliases are available:

-  [clj.webcam](https://github.com/hellonico/origami-javacv/blob/master/src/webcam.clj)
-  [clj.hello](https://github.com/hellonico/origami-javacv/blob/master/src/hello.clj)
-  [clj.smooth](https://github.com/hellonico/origami-javacv/blob/master/src/smooth.clj)
-  [clj.contours](https://github.com/hellonico/origami-javacv/blob/master/src/contours.clj)
-  [java.hello](https://github.com/hellonico/origami-javacv/blob/master/java/HelloCv.java)
-  [java.contour](https://github.com/hellonico/origami-javacv/blob/master/java/ContourCv.java)
-  [java.hough](https://github.com/hellonico/origami-javacv/blob/master/java/HoughLines.java)

### For example, run a webcam using JavaCV APIs.

```
(ns webcam
  (:import [org.bytedeco.javacv FrameGrabber CanvasFrame]))

(defn -main [& args]
  (let [grabber (FrameGrabber/createDefault 0)
        canvas (if (first args) (CanvasFrame. "Marcel" 0 nil) (CanvasFrame. "Webcam")) ]
    (.start grabber)
    (while (.isVisible canvas)
      (.showImage canvas (.grab grabber)))
    (.close grabber)))
```

# Deep Neural Network

## Tensorflow and Caffee Models..

There is now a [sibling project](https://github.com/hellonico/origami-dnn) showing how to use a caffee based network to identify object with origami and [mxnet](http://mxnet.incubator.apache.org/).

![](doc/detected.jpg) 

## Apache MxNET

There is a sample origami-mxnet project at https://github.com/hellonico/origami-mxnet, showing an integration of the two on a neural style network "image tranfer".

![](doc/mxnet.png)



# OpenCV compatibility Matrix

| Distribution    | Version    | Status | Comments                |
| --------------- | ---------- | :----: | ----------------------- |
| OSX             | Mojave     |   o    |                         |
| Windows         | 10         |   o    |                         |
| Linux           | glibc 2.19 |   o    |                         |
| Arm / Raspberry |            |   o    | No extra opencv modules |
| Arm64           |            |   o    | No extra opencv modules |
| Old Debian      | glibc 2.19 |   o    |                         |
| Android         | glibc 2.19 |   △    | Using precompiled, WIP  |

# Troubleshooting

## note to run on Apple/M1

Origami is using OpenCV behind the scenes, with a required version for the running CPU. This does not run well with default settings from sdkman, which is uses rosetta to translate intruction and thus, tells the JDK that the CPU is x64 instead of the expected m1. 

You can check this stackoverflow [java-jdk-for-apple-m1-chip](https://stackoverflow.com/questions/64788005/java-jdk-for-apple-m1-chip).
To fix this, basically, edit the sdkman config, making sure sdkman_rosetta2_compatible is set to false.

```bash
~> cat .sdkman/etc/config
sdkman_auto_answer=false
sdkman_auto_selfupdate=false
sdkman_insecure_ssl=false
sdkman_curl_connect_timeout=7
sdkman_curl_max_time=10
sdkman_beta_channel=false
sdkman_debug_mode=false
sdkman_colour_enable=true
sdkman_auto_env=false
sdkman_auto_complete=true

sdkman_rosetta2_compatible=false
```


## linux: video stream doesn't start

To get the stream from the webcam running, you would need the extra libv4l library on your system.

```
apt-get install libv4l-dev
```

or

```
pacman -S libv4l
```

## Ubuntu 14

... has a very outdated libstdc++, and the libopencv_java won't load. To install a newer libstdc++, you can try the following: (taken from: Stck

```
sudo add-apt-repository ppa:ubuntu-toolchain-r/test
sudo apt update
sudo apt-get install libstdc++6 
```

## Let's Encrypt Certificates

We are using [let's encrypt](https://letsencrypt.org/) for certificates to host the depending binaries. Old JDK versions (for example 1.8.80) are missing the root letsencrypt certificate and so the java runtime cannot validate our certificate.
To solve this, update to a recent version of the Java Development Kit.

```
Resolving javax.net.ssl.SSLHandshakeException: sun.security.validator.ValidatorException: PKIX path building failed Error?
```

[Resolving javax.net.ssl.SSLHandshakeException](https://stackoverflow.com/questions/9619030/resolving-javax-net-ssl-sslhandshakeexception-sun-security-validator-validatore/47952835#47952835)


# License

Copyright @Nicolas Modrzyk - 2017-2021
Eclipse Public License 