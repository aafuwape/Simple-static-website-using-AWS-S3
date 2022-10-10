# Simple-static-website-using-AWS-S3
Simple static website using AWS S3 using Static website hosting"


## First create a new bucket
**Bucket settings**  
Bucket name : simplestaticwebsite1882 (bucket names don't accept underscores,spaces, or caplital letters and must be globally unique
Disabled "Block Public Access settings for this bucket" and acked warning. This allows us to make it public
Tags
Project : simple static website
Default settings were used for the following :
- aws region
- object ownership
- Bucket versioning
- Encryption
- Advanced settings

**Next, make the bucket public.**  
When we setup the bucket, we only set the bucket to "Objects can be public" when we disabled "Block Public Access settings for this bucket". The objects are still private and need to be made public.

To make the objects public, go to the permissions tab and add the following s3 bucket policy. Pay attention to the arn

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicRead",
            "Effect": "Allow",
            "Principal": "*",
            "Action": [
                "s3:GetObject",
                "s3:GetObjectVersion"
            ],
            "Resource": "arn:aws:s3:::simplestaticwebsite1882/*"
        }
    ]
}
```

**Enable "Static website hosting"**  
Thereafter, enter the bucket and switch to the properties tab to enable "Static website hosting"
set the index document to index.html
set the error document to error.html

Now you have a bucket website endpoint
http://simplestaticwebsite1882.s3-website-us-east-1.amazonaws.com


**Finally upload the website files**  

now upload the index.html and error.html files


and that's it
You can now open the simple webpage by going to the bucket website endpoint.

