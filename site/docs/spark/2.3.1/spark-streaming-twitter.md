---
layout: page
title: Spark Streaming Twitter
description: Spark Streaming Twitter
group: nav-right
---
<!--
{% comment %}
Licensed to the Apache Software Foundation (ASF) under one or more
contributor license agreements.  See the NOTICE file distributed with
this work for additional information regarding copyright ownership.
The ASF licenses this file to you under the Apache License, Version 2.0
(the "License"); you may not use this file except in compliance with
the License.  You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
{% endcomment %}
-->

{% include JB/setup %}

A library for reading social data from [twitter](http://twitter.com/) using Spark Streaming. 

## Linking

Using SBT:

    libraryDependencies += "org.apache.bahir" %% "spark-streaming-twitter" % "2.3.1"

Using Maven:

    <dependency>
        <groupId>org.apache.bahir</groupId>
        <artifactId>spark-streaming-twitter_2.11</artifactId>
        <version>2.3.1</version>
    </dependency>

This library can also be added to Spark jobs launched through `spark-shell` or `spark-submit` by using the `--packages` command line option.
For example, to include it when starting the spark shell:

    $ bin/spark-shell --packages org.apache.bahir:spark-streaming-twitter_2.11:2.3.1

Unlike using `--jars`, using `--packages` ensures that this library and its dependencies will be added to the classpath.
The `--packages` argument can also be used with `bin/spark-submit`.

This library is cross-published for Scala 2.10 and Scala 2.11, so users should replace the proper Scala version (2.10 or 2.11) in the commands listed above.


## Examples

`TwitterUtils` uses Twitter4j to get the public stream of tweets using [Twitter's Streaming API](https://dev.twitter.com/docs/streaming-apis). Authentication information
can be provided by any of the [methods](http://twitter4j.org/en/configuration.html) supported by Twitter4J library. You can import the `TwitterUtils` class and create a DStream with `TwitterUtils.createStream` as shown below.

### Scala API

    import org.apache.spark.streaming.twitter._

    TwitterUtils.createStream(ssc, None)

### Java API

    import org.apache.spark.streaming.twitter.*;

    TwitterUtils.createStream(jssc);


You can also either get the public stream, or get the filtered stream based on keywords. 
See end-to-end examples at [Twitter Examples](https://github.com/apache/bahir/tree/master/streaming-twitter/examples)