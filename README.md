# scala

Scala combines object-oriented and functional programming in one concise, high-level language. Scala's static types help avoid bugs in complex applications, and its JVM and JavaScript runtimes let you build high-performance systems with easy access to huge ecosystems of libraries.<br>

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

# 6. Scala with Jupyter notebook
# 6-1. Apache Toree - Scala Notebookpache Toree
```
$ sudo docker pull jupyter/all-spark-notebook:c1b0cf6bf4d6
$ sudo docker run -it -p 8888:8888 --rm jupyter/all-spark-notebook:c1b0cf6bf4d6
```

# 6-2. spylon-kernel - Scala Notebook
```
$ sudo docker pull jupyter/all-spark-notebook:spark-3.1.2
$ sudo docker run -it -p 8888:8888 --rm jupyter/all-spark-notebook:spark-3.1.2
```

# 6-3. Convert RDD to a DataFrame
A DataFrame is an object that treats a data file like a database table on Spark. DataFrame has methods such as filter and join, and the API for handling these is the DataFrame API.<br>
> https://blog.serverworks.co.jp/introducing-pyspark-5 <br>
![dataframe.png](https://github.com/developer-onizuka/scala/blob/main/dataframe.png)

- input
```
// Spark - Dataset and Dataframe
// How to convert an existing RDD to a DataFrame
val data = Array(1, 2, 3, 4, 5)
val dist = sc.parallelize(data)
val df=dist.toDF()
df.show()
```
![spark.png](https://github.com/developer-onizuka/scala/blob/main/spark.png)

# 6-4. Create DataFrame as a defined Schema
- input
```
import org.apache.spark.sql.types._
import org.apache.spark.sql.functions._

val dataSchema = StructType(Array(
    StructField("id", IntegerType, true),
    StructField("name", StringType, true),
    StructField("price", DoubleType, true),
    StructField("country", StringType, true)))

val df = spark.read.format("csv").option("header","true").schema(dataSchema).load("fruits.csv")
df.printSchema()
df.show()
```
```
root
 |-- id: integer (nullable = true)
 |-- name: string (nullable = true)
 |-- price: double (nullable = true)
 |-- country: string (nullable = true)

+---+------+-----+-----------+
| id|  name|price|    country|
+---+------+-----+-----------+
|  1| Apple|10.99|      Japan|
|  2|Orange|11.99|      Japan|
|  3|Banana|12.99|      Japan|
|  4| Apple|10.99|        USA|
|  5|Orange|11.99|        USA|
|  6|Banana|12.99|     Taiwan|
|  7|Orange|11.99|     Israel|
|  8|Banana|12.99|Philippines|
+---+------+-----+-----------+
```
- fruits.csv
```
id,name,price,country
1,Apple,10.99,Japan
2,Orange,11.99,Japan
3,Banana,12.99,Japan
4,Apple,10.99,USA
5,Orange,11.99,USA
6,Banana,12.99,Taiwan
7,Orange,11.99,Israel
8,Banana,12.99,Philippines
```

# 6-5. Save as Table
- input
```
df.write.mode("overwrite").saveAsTable("fruitsTable")
```
```
val xDF = spark.read.table("fruitsTable");
xDF.show()
```
```
+---+------+-----+-----------+
| id|  name|price|    country|
+---+------+-----+-----------+
|  1| Apple|10.99|      Japan|
|  2|Orange|11.99|      Japan|
|  3|Banana|12.99|      Japan|
|  4| Apple|10.99|        USA|
|  5|Orange|11.99|        USA|
|  6|Banana|12.99|     Taiwan|
|  7|Orange|11.99|     Israel|
|  8|Banana|12.99|Philippines|
+---+------+-----+-----------+
```

# 6-6. Query for the saved table
```
val sqlDF = spark.sql("SELECT name, count(name) FROM fruitsTable GROUP By name")
sqlDF.show()
```
```
+------+-----------+
|  name|count(name)|
+------+-----------+
|Orange|          3|
|Banana|          3|
| Apple|          2|
+------+-----------+
```
