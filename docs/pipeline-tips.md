# Tips and Practices

- Actual image/video data and their annotations are stored in Blob Storages like the Amazon S3/Minio/Azure etc. 
- Generally, databases are used to store the metadata corresponding to the data stored in the blob storages such as the name, type of the image or sometimes even the entry (path of the data) in the
- So, for example in a key-value database or a document based database( we could have the "key" as the "name or type of the data" and its corresponding "value" as the path to the data folder/file stored in the S3 bucket).
- This key value pair is coded in our application while storing/updating/versioning the data and we can use this database to query the related data we need when necessary - and we can get the paths to the related files on the object storage and the use them.
  - Will need to look into how end to end experiment management tool or integration of tools would help achieve data and model versioning
    - For example: with tools like wandb with git and dvc

  
