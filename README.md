jdk8-backport
=============

Backport of some JDK8 features for JDK7

This contains backports of some features from [OpenJDK8].  Currently,
this includes:

 * java.util.Base64

The backported classes are packaged under `org.nkiesel.backport`,
so to use `java.util.Base64` from [OpenJDK8] in your code, use

```
import org.nkiesel.backport.java.util.Base64;
```

Source code is at [Github]

To build, you need [Maven] and JDK7.

Once you have the repository cloned, run "mvn package" to create the
Jar file.

The source code is copied from [OpenJDK8] and then slightly modified
to compile against JDK7.  This mostly involves adding imports for
other `java.util` classes and some minor changes to fix non-backward
compatible code (e.g. making soem variables explicitly `final`).  All
code was extracted from the tree produced by

```
% hg clone http://hg.openjdk.java.net/jdk8/jdk8/
% cd jdk8
% sh ./get_source.sh
```

The tests are directly from the [OpenJDK8] repository and thus do not
use JUnit.  Instead you have to run them directly (there might be a
better way to do this but I was too lazy to find out).  As an example,
use the following steps to run `TestBase64`:

```
% mvn package
% cd target/test-classes
% java -cp ../classes:. TestBase64
```


[OpenJDK8]: http://openjdk.java.net/projects/jdk8/
[Github]: https://github.com/nkiesel/jdk8-backport.git
[Maven]: http://maven.apache.org/index.html
