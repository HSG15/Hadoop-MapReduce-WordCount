
# 🧠 Hadoop MapReduce WordCount Project

This is a basic Hadoop MapReduce program to count the occurrences of words in a given input file.  
The program includes a Mapper, Reducer, and Driver class — all inside a single Java file.

---

## 📂 Project Structure

```
wordcount/
├── WordCount.java
├── wc.jar
└── output/          ← will be created by Hadoop
```

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
```

---

## 📄 Java Code

👉 [`WordCount.java`](https://github.com/HSG15/Hadoop-MapReduce-WordCount-Project/blob/main/WordCount.java)

---

## 🧪 Sample Output

```
bear    2
car     3
dear    4
```

---
## Steps to Execute

| Step | Action               | Command                                                                 |
|------|----------------------|-------------------------------------------------------------------------|
| 1    | Create project folder | `mkdir wordcount`                                                       |
| 2    | Write Java program    | `vi WordCount.java`                                                     |
| 3    | Compile code          | `javac -cp $(hadoop classpath) WordCount.java`                         |
| 4    | Package to JAR        | `jar cf wc.jar WordCount*.class`                                       |
| 5    | Prepare input file    | `vi dbzinput.txt`                                                       |
| 6    | Upload input to HDFS  | `hadoop fs -put ~/input/dbzinput.txt /user/harishankargiri16/input/`   |
| 7    | Run MapReduce job     | `hadoop jar wc.jar WordCount /input /output`                           |
| 8    | Check HDFS output     | `hadoop fs -ls /output_dbz`                                            |
| 9    | View result           | `hadoop fs -cat /output_dbz/part-r-00000`                              |

## Notes
- Replace the path `/user/harishankargiri16/` with your actual HDFS username if different.
- Make sure Hadoop is installed and configured properly before running the steps.


---

## 👨‍💻 Author

**Harishankar Giri**  
🔗 [GitHub @HSG15](https://github.com/HSG15)
