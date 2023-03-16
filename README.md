# scala

# 1. Install Java
```
$ sudo apt update
$ sudo apt install -y openjdk-8-jdk
```

# 2. Install Scala
```
$ curl -fL "https://github.com/coursier/launchers/raw/master/cs-x86_64-pc-linux.gz" | gzip -d > cs
$ chmod +x cs
$ ./cs setup -y
```

# 3. Install IDE
```
$ sudo snap install intellij-idea-community --classic
$ intellij-idea-community
```
![scala.png](https://github.com/developer-onizuka/scala/blob/main/scala.png)


# 4. Try to use
```
$ scala
Welcome to Scala 3.2.2 (1.8.0_362, Java OpenJDK 64-Bit Server VM).
Type in expressions for evaluation. Or try :help.
                                                                                                                        
scala> 1+2
val res0: Int = 3
                                                                                                                        
scala>
```
```
$ cat hello.scala 
object HelloWorld {
  def main(args: Array[String]) :Unit = {
    println("Hello World")
  }
}
```
```
$ scala hello.scala 
Hello World
```

# 5. Ansible Playbook
Also prepairing ansible playbook for scala.
```
$ git clone https://github.com/developer-onizuka/ansible
$ cd ansible
$ ansible-playbook scala.yaml
```
