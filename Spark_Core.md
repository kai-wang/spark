# Spark
## RDD
### SparkContext

### Create RDD
* parallelize

```
val xs = (1 to 100).toList
val rdd = sc.parallelize(xs)
```

* textFile

```
val lines = sc.textFile("README.md")
```

* wholeTextFiles
* sequenceFile

### RDD Transformation

* map
```
val lines = sc.textFile("README.md")
val lengths = lines.map{ l => l.length }
```
* filter
```
val lengths = lines.filter{ l => l.length > 50 }
```
* flatMap
```
val words = lines.flatMap{ l => l.split(" ") }
```
* mapPartitions
```
val lengths = lines.mapPartitions { iter => iter.map { l => l.length}}
```
* union
```
val r1 = sc.parallelize(('A' to 'Z').toList)
val r2 = sc.parallelize(('a' to 'a').toList)
val r3 = r1.union(r2)
```
* intersection
```
val r4 = r3.intersection(r2)
```
* substract
```
val r4 = r3.subtract(r2)
```
* distinct
```
val numbers = sc.parallelize(List(1, 2, 3, 4, 3, 2, 1))
val uniqueNumbers = numbers.distinct
```
* cartesian
```
val numbers = sc.parallelize(List(1, 2, 3, 4))
val alphabets = sc.parallelize(List("a", "b", "c", "d"))
val pairs = numbers.cartesian(alphabets)
```

```
Array[(Int, String)] = Array((1,a), (1,b), (1,c), (1,d), (2,a), (2,b), (2,c), (2,d), (3,a), (3,b), (3,c), (3,d), (4,a), (4,b), (4,c), (4,d))
```

* zip
```
val numbers = sc.parallelize(List(1, 2, 3, 4))
val alphabets = sc.parallelize(List("a", "b", "c", "d"))
val pairs = numbers.zip(alphabets)
```
* zipWithIndex
```
val alphabets = sc.parallelize(List("a", "b", "c", "d"))
val pairs = numbers.zipWithIndex
```

```
Array[(String, Long)] = Array((a,0), (b,1), (c,2), (d,3))
```
* groupBy
* keyBy
* sortBy
* pipe
* randomSplit
* coalesce
* repartition
* sample
* keys
* values
* mapValues
* join
* leftOuterJoin
* rightOuterJoin
* fullOuterJoin
* sampleByKey
* subtractByKey
* groupByKey
* reduceByKey

### Actions
* collect
* count
* countByValue
* first
* max
* min
* take
* takeOrdered
* top
* fold
* reduce
* countByKey
* lookup
* mean
* sum
* stdev
* variance

### Save, Persist & Cache

* saveAsTextFile
* saveAsObjectFile
* saveAsSequenceFile
* cache
* persist

### Spark Jobs



