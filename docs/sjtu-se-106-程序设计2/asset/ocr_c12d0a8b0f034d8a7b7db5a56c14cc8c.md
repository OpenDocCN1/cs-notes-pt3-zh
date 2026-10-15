# The Bucket Hashing Strategy

+   - One common strategy for implementing a map is to use the hash code for each key to select an index into an array that will contain all the keys with that hash code. Each element of that array is conventionally called a **bucket**.
+   
+   - In practice, the array of buckets is smaller than the number of hash codes, making it necessary to convert the hash code into a bucket index, typically by executing a statement like

```
int index = hashCode(key) % nBuckets;
```

+   - The value in each element of the bucket array cannot be a single key/value pair given the chance that different keys fall into the same bucket. Such situations are called **collisions**.
+   
+   - To take account of the possibility of collisions, each elements of the bucket array is a linked list of the keys that fall into that bucket, as illustrated on the next slide.