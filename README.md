
---

## 🛠️ Run Instructions (Single Copy-Paste Block)

```bash
# Step 1: Create working directory
mkdir wordcount && cd wordcount

# Step 2: Download Java source code
wget https://raw.githubusercontent.com/HSG15/Hadoop-MapReduce-WordCount-Project/main/WordCount.java

# Step 3: Compile Java program
javac -cp $(hadoop classpath) WordCount.java

# Step 4: Package it into a JAR file
jar cf wc.jar WordCount*.class

# Step 5: Create sample input locally
cd ..
mkdir input
echo -e "dear bear car\ncar car bear\ndear dear dear" > input/dbzinput.txt

# Step 6: Upload file to HDFS
hadoop fs -mkdir -p /user/harishankargiri16/input
hadoop fs -put input/dbzinput.txt /user/harishankargiri16/input/

# Step 7: Run the MapReduce job
cd wordcount
hadoop jar wc.jar WordCount /user/harishankargiri16/input/dbzinput.txt /user/harishankargiri16/output_dbz

# Step 8: Check results
hadoop fs -cat /user/harishankargiri16/output_dbz/part-r-00000

# Sample Output
bear    2
car     3
dear    4

