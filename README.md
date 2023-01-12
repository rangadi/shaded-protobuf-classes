# shaded-protobuf-classes

This project creates shaded Java classes for Protobuf files placed in
[src/main/protobuf](src/main/protobuf) directory. These classes are suitable for use with
[Protobuf functions in Spark](https://github.com/apache/spark/blob/master/python/pyspark/sql/protobuf/functions.py).

Java class support in Spark Protobuf connector requires the classes to be shaded.
Specifically references to `com.google.protobuf.*` classes should be rewritten to
`org.sparkproject.spark-protobuf.protobuf.*`.

### How to create shaded Java classes for your Protobufs

  * Clone this repo
  * Add Protobuf files to `src/main/protobuf` directory.
  * Run `mvn clean package`
  * Once the above is successful, `target/shaded-protobuf-classes-1.0.jar` contains shaded Java classes.
  
### How to verify proper shading

The jar file can be inspected with a Java decompiler like [JD-GUI](http://java-decompiler.github.io/).
The generated classes should have import statements that look similar to
`import org.sparkproject.spark-protobuf.protobuf.AbstractMessage;`.
The following screenshot for `AppEvent` class illustrates this:


<img width="600" alt="java decompiler screenshot for AppEvent" src="https://user-images.githubusercontent.com/502522/211994068-aab71ad7-e655-4f94-9b62-04fb5e67f328.png">
