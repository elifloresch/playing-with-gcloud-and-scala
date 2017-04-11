# Playing with Gcloud and Scala

## Setup the fun in GCloud
1. Set up a [GCloud project](https://cloud.google.com/dataproc/docs/guides/setup-project)
2. Create a [Cloud Storage bucket](https://console.cloud.google.com/project/_/storage)
3. Create a [Cloud Dataproc cluster](https://cloud.google.com/dataproc/docs/guides/create-cluster)

## Scala Code
1. Create a HelloWorld Scala Object
2. Package your project
    * Using sbt
        ```sbt package```
    * This should generate a jar file in target/scala-2.10 directory
        

## GCloud Fun
1. Copy jar to Cloud Storage 
    ```gsutil cp [path-to]/playing-with-gcloud-and-scala_2.10-0.1-SNAPSHOT.jar gs://<bucket_name>/```
2. Submit your job to a cluster
    * Go to ```https://console.cloud.google.com/dataproc/jobs?project=[ProjectName]```
    * Click on Submit Job
        * Fill up form:
            * Cluster: Select your cluster's name from the cluster list
            * Job type: Spark
            * Main class or jar: gs://your-bucket-name/playing-with-gcloud-and-scala_2.10-0.1-SNAPSHOT.jar
    * Click on Submit
3. Click the Job ID to open the Jobs page, where you can view the job's driver output
    * You should see something like:
        ```
           Hello, world!
           Job output is complete
        ```

## Final Steps
1. Shutdown your cluster
    * gcloud dataproc clusters delete <cluster-name>
    * gsutil rm gs://<bucket-name>/playing-with-gcloud-and-scala_2.10-0.1-SNAPSHOT.jar
2. Try a new job! 
    * Example: Write and run Spark Scala code using the cluster's spark-shell REPL from [here](https://cloud.google.com/dataproc/docs/tutorials/spark-scala)
        
            
## Useful commands
* List your projects: ```gcloud projects list```
* List clusters in current project: ```gcloud dataproc clusters list```

## Useful links
* To see all your clusters go [here](https://console.cloud.google.com/dataproc/clusters/)

## Reference
* [Tutorial](https://cloud.google.com/dataproc/docs/tutorials/spark-scala)