## Windows 10 Setup
### Install JDK (java development kit)
- Download Java SE Development Kit 8u102
### Install Spark
- spark.apache.org - `Spark 2.3.3.tgz`
- Extract and copy to C:\spark_2.3.3
- Modify conf\log4j.properties.template
	- rename to log4j.properties
	- log4j.rootCategory=ERROR
#### www.rarlab.com/down.load
- WinRAR x64 version
### winutils
- sundog-spark.s3.amazonaws.com/winutils.exe
	- Copy to C:\winutils\bin
### Setup Environment Variables
- Users variables
	- SPARK_HOME: C:\spark_2.3.3
	- JAVA_HOME: C:\Program Files\Java\jdk1.8.0_102
	- HADOOP_HOME: C:\winutils
	- Path
		- Edit
			- New: %SPARK_HOME%\bin
			- New: %JAVA_HOME%\bin
### scala IDE
- scala-ide.org
	- Eclipse
## Local Test
- Command Window
	- c:spark_2.3.3
		- spark-shell
		- val rdd=sc.textFile("README.md")
		- rdd.count()
### 
## Scala Project
### Get Movie Data
- grouplens.org
	- dataset
		- ml-100k.zip (MovieLens 100K Dataset)
		- u.data contains all data

#### Get Code Example
- media.sundog-soft.com/SparkScala/SparkScala.zip

#### Eclispe
- New Scala Project
	- New (Java) Package
		- Name: com.sundogsoftware.spark
	-  Import (src code)
		- General
			- File System
				- Spark Scala from above
					- RatingsCounter.scala
	- Project Properties
		- Java Build Path
			- Library
				- Add External JARs
					- C:\spark_2.3.3	\jars
	- Fix incompatible version of scala(2.11.11) vs spark(2.3.3)
		- Project Properties
			- Scala Compiler
				- use project settings
				- Fixed Scala Installation: 2.11.11 (built-in)
	- Run
		- Run Configurations
			- Scala Application
				- Name: RatingsCounter
				- Main class: `=package name + scala object name`: com.sundogsoftware.spark.RatingsCounter
### Using Cluster Manager
#### Eclipse
- package
	- Export
		- Java JAR file
			- save into any location
#### Command Window
- Go to where you saved the jar file location
	- spark-submit --class com.sundogsoftware.spark.RatingsCounter RatingsCounter.jar
