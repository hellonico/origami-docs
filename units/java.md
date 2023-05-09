
# Using Maven working in Java

If you have [maven](https://maven.apache.org/) installed, you can copy paste the script below, and a new ready to use origami set up will be ready for you in the cvj folder.

```bash
curl -s http://repository.hellonico.info/repository/vendredi/origami/gen.sh | bash
```

or, by typing everything yourself:

```bash
mvn org.apache.maven.plugins:maven-archetype-plugin:2.4:generate \
 -DarchetypeArtifactId=maven-archetype \
 -DarchetypeGroupId=origami \
 -DarchetypeVersion=4.2 \
 -DarchetypeCatalog=https://repository.hellonico.info/repository/hellonico/ \
 -Dversion=1.0-SNAPSHOT \
 -DgroupId=hello \
 -DartifactId=cvj
```

 Which can be used as is in your favorite editor, or run on the command line with:

```bash
mvn compile exec:java
```

# Examples

The generated java project contains a few ready to use OpenCV examples.

## Hello OpenCV

This is the most basic. *Origami.init()* makes sure OpenCV is initialized properly.

```
Origami.init();
Mat hello = Mat.eye(3, 3, CvType.CV_8UC1);
System.out.println(hello.dump());
```

## Guess my age

Shows how to use a neural network and applies it to an image. Here we use a network that determines the age of the person in the picture.

```
List<?> _list = origami.Dnn.readNetFromSpec("networks.caffe:convnet-age:1.0.0");
        Net net = (Net) _list.get(0);
        /*
         * readNetFromSpec returns
         * 
         * 0: Net object
         * 
         * 1: Options related to the way the image blob should be created
         * 
         * 2: labels
         */
        List<String> labels = (List<String>) _list.get(2);

        final String imageFile = args.length > 0 ? args[0] : "src/main/resources/jeunehomme.jpg";
        Mat image = imread(imageFile);
        Mat inputBlob = blobFromImage(image, 1.0, new Size(256, 256));
        net.setInput(inputBlob);
        net.setPreferableBackend(Dnn.DNN_BACKEND_OPENCV);

        /*
         * Get Result and Output
         */
        Mat result = net.forward();
        result = result.reshape(1, 1);
        // System.out.println(result.dump());
        Core.MinMaxLocResult minmax = minMaxLoc(result);
        System.out.println("Age range:" + labels.get((int) minmax.maxLoc.x));
```


## WebCam

Isn't that the easiest way to start a streaming WebCam on the JVM?

```
Origami.init();
new Camera().run();
```
