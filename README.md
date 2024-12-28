## Additions to this fork

This fork of ZX0-Java adds a header at the start of the packed file, so a program
trying to depack the files does not need external information (such as
original file size or delta value). All values are in big endian format and
the header is as follows:

|offset|size|description|
|:---: |:--:|:--:       |
|0     |4   |Magic value of 0x5a583021 or `ZX0!`|
|4     |4   |packed size|
|8     |4   |unpacked size|
|12    |2   |delta      |

To build, download Java SDK and put it on your PATH.
Then download [Maven](https://maven.apache.org/download.cgi) (also put it in your PATH) and run `mvn verify` in the base folder.
Finally, to create the "exe" version (still needs the Java SDK) download [install4j](https://sourceforge.net/projects/launch4j/) and load the `launch4j` from the root of this repo. Adjust the output file. Optionally add the Java SDK bin path to the "Bundled JRE path" in the "JRE" tab. Press the gear icon and it should do the trick.

# ZX0-Java

**ZX0-Java** is a multi-thread implementation of the
[ZX0](https://github.com/einar-saukas/ZX0) data compressor in
[Java](https://www.java.com/).


## Requirements

To run this compressor, you must have installed [Java](https://www.java.com/) 8
or later.


## Usage

To compress a file such as "Cobra.scr", use the command-line compressor as
follows:

```
java -jar zx0.jar Cobra.scr
```

Java 8 memory allocation is limited to (at most) 1Gb by default. You can use
parameter "-Xmx" to increase maximum memory allocation, for instance:

```
java -Xmx2G -jar zx0.jar Cobra.scr
```

This compressor uses 4 threads by default. You can use parameter "-p" to
specify a different number of threads, for instance:

```
java -jar zx0.jar -p2 Cobra.scr
```

All other parameters work exactly like the original version. Check the official
[ZX0](https://github.com/einar-saukas/ZX0) page for further details.


## License

The Java implementation of [ZX0](https://github.com/einar-saukas/ZX0) was
authored by **Einar Saukas** and it's available under the "BSD-3" license.


## Links

* [ZX0](https://github.com/einar-saukas/ZX0) - The original version of **ZX0**,
by the same author.

* [ZX0-Kotlin](https://github.com/einar-saukas/ZX0-Kotlin) - A similar
multi-thread data compressor for [ZX0](https://github.com/einar-saukas/ZX0)
in [Kotlin](https://kotlinlang.org/), by the same author.

* [ZX5-Kotlin](https://github.com/einar-saukas/ZX5-Kotlin) - A similar
multi-thread data compressor for [ZX5](https://github.com/einar-saukas/ZX5)
in [Kotlin](https://kotlinlang.org/), by the same author.
