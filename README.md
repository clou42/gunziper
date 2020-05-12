# gunziper

A plugin for [Burp Suite](https://portswigger.net/burp/) which enables you to:
* "unpack" requests/responses (e.g. do an base64decode and afterwards a java deserialisation)
* the possibility to gather e.g. a CSRF token from responses and automatically insert it in any request (without the need to do an extra request with burps macro functionality)
* half automatically compare hundreds/thousands of responses for differences
  * Imagine you used intruder to test 10 GET parameters with payloads, and the application simply reflects the whole URL somewhere in the response. Of course, there might be XSS, but what about other vulnerabilities like SQL, XXE, ... Sorting for the response size will not trivially point to relevant requests, so intruder comparer comes into play. With it, you can define a regex which strips parts of the response (e.g. the reflected URL) and then iterates over all responses and does a comparison of the last and current response, and if there are some differences, it will show a diff window similar to burp's comparer.

## Pre-built JARs

Pre-built JAR files are available in [Releases](https://github.com/f-block/gunziper/releases)

## Build from source

Build JAR files from source:

```bash
wget https://github.com/f-block/gunziper/archive/master.zip
unzip master.zip
cd gunziper-master
gradle jar
```

## Dependencies

* [xstream](http://x-stream.github.io/index.html)
* [kxml2](https://sourceforge.net/projects/kxml/files/kxml2/2.3.0/)
* [java-diff-utils](http://code.google.com/p/java-diff-utils/)
* [Diff Match and Patch](http://code.google.com/p/google-diff-match-patch)
