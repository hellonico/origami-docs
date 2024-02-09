# WebCam

With a *deps.edn* like below:

```
{:mvn/repos
   {"vendredi" {:url "https://repository.hellonico.info/repository/hellonico/"}}
 :deps
   {origami {:mvn/version "4.7.0-0"}}}
```

You can start a simple streaming web cam with:

```clojure
(require '[opencv4.core :refer :all] '[opencv4.utils :as u])
; then you can start a simple no-op clojure function
(u/simple-cam-window identity)
```

# Stream Input

You can also add settings to which device you are streaming from, and other settings like for example add fps info. Below we stream from device with id 0:

```clojure
(u/simple-cam-window {:frame {:fps true} :video {:device 0}} identity)
```

Note that you can enter a filename, or even an http(s) url to the video device. Here we load a video of Marcel le chat.

```clojure
(u/simple-cam-window 
  {:video {:device "http://www.hellonico.info/marcel/video-1617099963.mp4"}} 
  identity)
```

Settings can also be read from an external cam.edn file:

```clojure
; content of cam.edn
{:frame {:fps true} :video {:device 0}}

; and then load this in the cam window
(u/simple-cam-window "cam.edn" identity)
```

# Apply a function to the stream

You can specify a function to apply to each frame read by the webcam

```clojure
; in the clojure repl with  clj or lein
(require '[opencv4.core :refer :all] '[opencv4.utils :as u])

(def my-function (fn[x] (-> x (flip! -1))))
(u/simple-cam-window my-function)
```

# Real time Function Update

To update the function at the repl in real time, you can write an intermediate function, and update the original my-function when needed.

```clojure
; in the clojure repl with  clj or lein
(require '[opencv4.core :refer :all] '[opencv4.utils :as u])

(def my-function (fn[x] (-> x (flip! -1))))
(def inter (fn[x] (my-function x)))
(u/simple-cam-window inter)
; then
(def my-function (fn[x] (-> x (flip! 1))))

; and the function applied to the stream will be changed in real-time
```

# Origami filters

With a Clojure *deps.edn* like below, or a template of your choice.

```clojure
{:mvn/repos
   {"vendredi" {:url "https://repository.hellonico.info/repository/hellonico/"}}
 :deps
   {origami-dnn {:mvn/version "0.1.13"}
    origami/filters {:mvn/version "1.12"}}}
```

You can start a web cam with:

```clojure
(require '[opencv4.core :refer :all] '[opencv4.utils :as u])
; then you can start a simple no-op clojure function
(u/simple-cam-window {:frame {:fps true}} identity)
; or pass in a java class
(u/simple-cam-window {:frame {:fps true}} "[{:class origami.filters.NoOPFilter}]")
; or a more fun one
(u/simple-cam-window {:frame {:fps true}} [{:class origami.filters.Cartoon}])
```

You can also write the content of the filter string in a separate edn file. 
```
; Supposing filters.edn content is the one line below
[{:class origami.filters.Cartoon}]

; then you can load that filter directly from the string
(u/simple-cam-window "filters.edn")
```

Next step would be to combine those filters. The edn file is just an array of filters applied one after the other:
```clojure
; new content of filters.edn
[{:class origami.filters.Resize :factor 0.5}
 {:class origami.filters.Gray}
 {:class origami.filters.FPS}]
```

And again used with:

```clojure
(u/simple-cam-window "filters.edn")	
```

And that would resize the webcam stream by half, turn it to gray, and add FPS information.