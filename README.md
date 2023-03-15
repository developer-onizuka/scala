# scala

```
$ sudo apt update
$ sudo apt install -y openjdk-8-jdk
```
```
$ java -version
openjdk version "1.8.0_362"
OpenJDK Runtime Environment (build 1.8.0_362-8u362-ga-0ubuntu1~20.04.1-b09)
OpenJDK 64-Bit Server VM (build 25.362-b09, mixed mode)
```
```
$ curl -fL https://github.com/Virtuslab/scala-cli/releases/latest/download/scala-cli-x86_64-pc-linux.gz | gzip -d > scala-cli
$ chmod +x scala-cli
$ sudo mv scala-cli /usr/local/bin/scala-cli
```
```
$ scala-cli --version
Scala CLI version: 0.2.0
Scala version (default): 3.2.2
```
```
$ curl -fL "https://github.com/coursier/launchers/raw/master/cs-x86_64-pc-linux.gz" | gzip -d > cs
$ chmod +x cs
$ ./cs setup
Checking if a JVM is installed
Found a JVM installed under /usr/lib/jvm/java-8-openjdk-amd64/jre.

Checking if ~/.local/share/coursier/bin is in PATH
  Should we add ~/.local/share/coursier/bin to your PATH via ~/.profile? [Y/n] y

Checking if the standard Scala applications are installed
  Installed ammonite
  Installed cs
  Installed coursier
  Installed scala
  Installed scalac
  Installed scala-cli
  Installed sbt
  Installed sbtn
  Installed scalafmt
  
$ coursier java --available
```

```
$ scala
Welcome to Scala 3.2.2 (1.8.0_362, Java OpenJDK 64-Bit Server VM).
Type in expressions for evaluation. Or try :help.
                                                                                                                        
scala> 1+2
val res0: Int = 3
                                                                                                                        
scala>
```

