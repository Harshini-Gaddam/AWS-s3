## Making S3 Objects Public

To make objects in your Amazon S3 bucket publicly accessible, follow these steps:

1. **Open S3 Console**: Log into AWS and navigate to the S3 service.

2. **Select Bucket**: Click on the bucket containing the objects.

3. **Edit Bucket Policy**:
   - Go to the "Permissions" tab
   - Under "Bucket policy", click "Edit"
   - Add this policy (replace `your-bucket-name`):
     ```json
     {
         "Version": "2012-10-17",
         "Statement": [
             {
                 "Sid": "PublicReadGetObject",
                 "Effect": "Allow",
                 "Principal": "*",
                 "Action": "s3:GetObject",
                 "Resource": "arn:aws:s3:::your-bucket-name/*"
             }
         ]
     }
     ```

4. **Allow Public Access**:
   - In "Permissions", find "Block public access"
   - Click "Edit" and uncheck "Block all public access"
   - Save changes

5. **Set Object ACLs**:
   - For existing objects: Select object(s) > "Actions" > "Make public using ACL"
   - For new uploads: Set ACL to "Public Read" when uploading

6. **Access Public Objects**:
   Objects are now accessible at:
   `https://your-bucket-name.s3.amazonaws.com/path/to/object`

**Note**: Making objects public means anyone can access them. Use with caution and only for content intended to be public.
