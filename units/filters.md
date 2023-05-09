# Filters Loading

In  general you can load the filters in any language using Clojure  dynamic  loading. 
The  filters can be defined:
- as a string
or
- as a  file containing the filters in  edn notation. (similar to json but easier to handle)

Here are a  few examples, and be sure to check the [full list](filters/filters.md) available from the documentation.

### Show date dynamically

```clojure
[{:class origami.filters.DynamicAnnotate :point "0,200" :text "(str (java.util.Date.))"}]
```

### Add the main ip address of the streaming device

```clojure
[{:class origami.filters.DynamicAnnotate :text "(java.net.InetAddress/getLocalHost)"}]
```

###  Multiple filters piped one after the one

Here:
- Resize, 
- Apply Yolo Detection and 
- add FPS information

```clojure
[{:class origami.filters.Resize :factor 0.3}
 {:class origami.filters.MyYolo$V3}
 {:class origami.filters.FPS}]
```

### How to  use  the ClojureFilter (inlined clojure code executed)

```clojure
[{:class origami.filters.ClojureFilter
   :fn "(fn[mat] (org.opencv.imgproc.Imgproc/applyColorMap mat mat 3) mat)"}
  ]
```

### Load filter definition through http and refresh.

Here the filter content is  retrieved through http and refresh every 2 seconds.

```clojure
[{:class origami.filters.HttpGet :interval 2 :url "http://localhost:3000"}]
```

