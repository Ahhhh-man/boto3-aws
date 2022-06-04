# AWS boto3 python module

## Provision environment
Setup credentials.
```
touch ~/.aws/credentials
```
Paste the following.
```
[default]
aws_access_key_id = YOUR_ACCESS_KEY_ID
aws_secret_access_key = YOUR_SECRET_ACCESS_KEY
```
Create the config file.
```
touch ~/.aws/config
```
Paste the following.
```
[default]
region = YOUR_PREFERRED_REGION
```

Install python 3.6 or later; support for Python 3.5 and earlier is deprecated.
```
sudo apt update
sudo apt install software-properties-common
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt update
sudo apt install python3.6
python --version
```

Install awscli.
```
sudo pip install awscli
```
Install boto3.
```
sudo pip install boto3
```
Verify installation.
```
python
> import boto3
```
<br>
<hr/>

## A sample of boto3 functionality

### Create an Amazon S3 bucket
```python
import boto3

s3 = boto3.client('s3')
s3.create_bucket(Bucket='my-bucket')
```

### Add/Upload to an Amazon S3 bucket
```python
import boto3

s3 = boto3.client('s3')
s3.download_file("<bucket-name>", 'img1.jpg', 'img2.jpg')
```

### List objects in an Amazon S3 bucket
```python
import boto3

s3 = boto3.resource('s3')
bucket = s3.Bucket('my-bucket')
for item in bucket.objects.all():
    print(item.key)
```

### Delete objects in an Amazon S3 bucket
```python
import boto3

s3 = boto3.client('s3')
s3.delete_object(Bucket="<bucket-name>", Key='img1.jpg')
```

### Terminate an Amazon S3 bucket
```python
import boto3

s3 = boto3.client('s3')
s3.delete_bucket(Bucket=bucket_name)
```
**Remark.** You need to have an empty bucket to delete it.