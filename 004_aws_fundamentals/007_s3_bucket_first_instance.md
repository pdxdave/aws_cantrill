# S3 Buck First Instance

![s3_bucket_first_01](../assets/s3_bucket_first_01.png)
1. Go to the S3 console and then Buckets > Create bucket.
2. Give the bucket a unique name.  Remember, it must be unique globally. ```koalacampaign092375461```
3. Select a region
4. Will hit Object Ownership later

![s3_bucket_first_02](../assets/s3_bucket_first_02.png)
1. S3 buckets are private by default.  Only the general AWS account and the account root user have access.
2. You can grant access to all users, even unauthenticated users, but that's not a good idea.
3. Disabling the "Block all public access" doesn't give it public access.  It just means you can give it public access.

![s3_bucket_first_03](../assets/s3_bucket_first_03.png)