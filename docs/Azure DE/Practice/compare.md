Question #28Topic 1
You plan to implement an Azure Data Lake Storage Gen2 container that will contain
CSV files. The size of the files will vary based on the number of events that occur per
hour.
File sizes range from 4 KB to 5 GB.
You need to ensure that the files stored in the container are optimized for batch

DATAWOLFS.COM -- DP203 DUMPS
FOLLOW US : DATAWOLFS.COM | LINKEDIN | YOUTUBE

Follow Us: Datawolfs.com | Youtube | Linkedin 39
processing.
What should you do?
• A. Convert the files to JSON
• C. Compress the files
• D. Merge the files
Hide Solution
Correct Answer: B
Avro supports batch and is very relevant for streaming.

Note: Avro is framework developed within Apacheג€TMs Hadoop project. It is a row-
based storage format which is widely used as a serialization process. AVRO stores its

schema in JSON format making it easy to read and interpret by any program. The data
itself is stored in binary format by doing it compact and efficient.
Reference:
https://www.adaltas.com/en/2020/07/23/benchmark-study-of-different-file-format/


