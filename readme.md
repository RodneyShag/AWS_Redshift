<p align="center">
    <img src="images/redshift_logo.png">
</p>

- [Tutorial by Edureka](#tutorial-by-edureka)
- [References](#references)



# [Tutorial by Edureka](https://www.youtube.com/watch?v=fc5WPKnbam8)

[What is a data warehouse?](https://youtu.be/fc5WPKnbam8?t=75) - a repository where data generated from your organization
s operational systems is collected, transformed, and stored.

[What is Redshift?](https://youtu.be/fc5WPKnbam8?t=349) - a parallel, column-oriented database for analyzing data in your data warehouse.

[What are clusters and nodes?](https://youtu.be/fc5WPKnbam8?t=381) - _nodes_ are a collection of compute resources. A group of nodes is called a _cluster_. Each cluster runs a Redshift engine, and it contains 1+ databases.

![Clusters and Nodes](./images/clustersAndNodes.png)

[What is a leader node?](https://youtu.be/fc5WPKnbam8?t=397) - receives queries from client applications. It coordinates the parallel execution of a query using 1+ compute nodes. The leader node also aggregates the results from the compute nodes and sends it back to the client appliation.

[What is a compute node?](https://youtu.be/fc5WPKnbam8?t=422) - compute resources that are used to process queries that the _leader node_ sends it. Compute nodes can transfer data amongst themselves to solve queries.

[What are node slices?](https://youtu.be/fc5WPKnbam8?t=435) - _compute nodes_ are divided into _node slices_. Each slice receives memory and disk space. Slices work in parallel to perform operations.

[How do clients communicate with Redshift?](https://youtu.be/fc5WPKnbam8?t=466) - client applications  communicate with the _Leader Node_ using either:

1. JDBC (Java Database Connectivity Driver) - an API for Java, or
1. ODBC (Other Database Connectivity Driver) - uses SQL to interact with Leader Node

[What are some settings you select during Redshift cluster creation?](https://youtu.be/fc5WPKnbam8?t=598) - type of node you want, number of nodes, the VPC where you want to create your data warehouse, etc.

[How does Redshift autoscale up and down?](https://youtu.be/fc5WPKnbam8?t=657) - it just increases or lowers the number of compute nodes.

[Is Redshift row or column storage?](https://youtu.be/fc5WPKnbam8?t=730) - column storage.

[What are some benefits of column storage?](https://youtu.be/fc5WPKnbam8?t=817) Since the data is stored next to each other, we get:
1. Improved Data compression
1. Faster queries and updates on columns

[What is a Data Lake?](https://youtu.be/fc5WPKnbam8?t=962) - a storage repository that holds a vast amount of raw data in it's native format until it's needed (CSV, Parquet, TSV, RCFile, etc.)

[What is ETL?](https://youtu.be/fc5WPKnbam8?t=977) - A sample ETL is when you _Extract, Transform, Load_ data from a data lake into Redshift. This is time-consuming, compute-intensive, and costly (due to the need of growing your clusters in Redshift).

[What is _Amazon Redshift Spectrum_?](https://youtu.be/fc5WPKnbam8?t=1012) - Instead of doing ETL jobs, you can use _Amazon RedShift Spectrum_ to directly query data in s3 or a data lake, without unnecessary data movement.

[How is data backed up in Redshift?](https://youtu.be/fc5WPKnbam8?t=1034) - Redshift offers backup and recovery. As soon as data is stored in Redshift, a copy of that data is sent to s3 through a secure connection. If you lose your data, you can restore it easily using s3.

[Does Redshift provide encryption?](https://youtu.be/fc5WPKnbam8?t=1059) - yes.

[What software do you need to install to use Redshift?](https://youtu.be/fc5WPKnbam8?t=1097)

1. SQL Workbench - this is where you do queries
1. JDBC Driver - enables the client application to communicate with Redshift
1. Also, Java Runtime should be enabled on your OS

[How create a Redshift cluster in AWS Console?](https://youtu.be/fc5WPKnbam8?t=1230) - in the AWS Console, go to _Amazon Redshift_ and click _Quick launch cluster_ (fastest way) or _Launch cluster_ (more versatile way)

[When creating a Redshift cluster, what is the default port?](https://youtu.be/fc5WPKnbam8?t=1348) - they set it to `5439` for us. We use this port number later.

[How is a database created in Redshift?](https://youtu.be/fc5WPKnbam8?t=1459) - when we used the "Quick launch cluster" option, a default database called `dev` is created for us.

[What URL does SQL workbench need to connect to the cluster](https://youtu.be/fc5WPKnbam8?t=1571) - either a JDBC URL or ODBC URL. Both can be found in AWS Console's Redshift dashboard, under _Clusters_.

[How create tables in Redshift?](https://youtu.be/fc5WPKnbam8?t=1669) - can use a sample database from AWS documentation (which is a bunch of `create table` commands to copy/paste)

[How copy data for a database from s3 into Redshift?](https://youtu.be/fc5WPKnbam8?t=1742)

You can do something like:

```sql
copy users from 's3://awssamplebuswest2/tickit/allusers_pipe.txt'
credentials 'aws_iam_role=<iam-role-arn>'
delimiter '|' region 'us-west-2';
```
- This copies to the table `users` from a given path.
- You also have to provide an IAM role as credentials
- The `delimiter` is what separates the fields of the columns
- `region` is where your s3 bucket is located

[How perform queries on this new data?](https://youtu.be/fc5WPKnbam8?t=1878) - use SQL workbench.

[How see previous queries you've performed?](https://youtu.be/fc5WPKnbam8?t=1981) - In AWS Console, go to your Redshift cluster and click the _Queries_ tab.

### References

#### References used in this repo

[Amazon Redshift Tutorial | AWS Tutorial for Beginners | AWS Certification Training | Edureka](https://www.youtube.com/watch?v=fc5WPKnbam8) - good beginner tutorial.

#### References - Deprecated

- [Deep Dive on Amazon Redshift - AWS Online Tech Talks](https://www.youtube.com/watch?v=Hur-p3kGDTA) - too advanced.
