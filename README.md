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
