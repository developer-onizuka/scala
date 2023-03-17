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

# 6. Apache Toree - Scala Notebookpache Toree
```
$ sudo docker pull jupyter/all-spark-notebook:c1b0cf6bf4d6
$ sudo docker run -it -p 8888:8888 --rm jupyter/all-spark-notebook:c1b0cf6bf4d6
```

# 7. spylon-kernel - Scala Notebook
```
$ sudo docker pull jupyter/all-spark-notebook:spark-3.1.2
$ sudo docker run -it -p 8888:8888 --rm jupyter/all-spark-notebook:spark-3.1.2
```
# 8. Convert RDD to a DataFrame
```
// Spark - Dataset and Dataframe
// How to convert an existing RDD to a DataFrame
val data = Array(1, 2, 3, 4, 5)
val dist = sc.parallelize(data)
val df=dist.toDF()
df.show()
```
![spark.png](https://github.com/developer-onizuka/scala/blob/main/spark.png)

# 9. Create DataFrame as a defined Schema
```
import org.apache.spark.sql.types._
import org.apache.spark.sql.functions._

val dataSchema = StructType(Array(
    StructField("id", IntegerType, true),
    StructField("name", StringType, true),
    StructField("price", DoubleType, true),
    StructField("country", StringType, true)))

val df = spark.read.format("csv").option("header","true").schema(dataSchema).load("fruits.txt")
df.printSchema()
df.show()
```
