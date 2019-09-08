#cross account s3 access

Provider s3 bucket : documents-kiwony
731146858750


Requester s3 bucket : documents-backup-kiwony
Account id : 664695030410
Canonical Id : 73478f1106ef73c64360a9ba0f345f3e606c426aa9f6d15fe4d0421a048b78be

Requester 
- Create policy : s3-cross-access-from-documents-kiwony-731146858750
```bash
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "s3:GetObject",
                "s3:PutObject",
                "s3:PutObjectAcl"
            ],
            "Resource": "arn:aws:s3:::documents-kiwony/*"
        }
    ]
}
```


Provider
- S3 -> Permissions -> Bucket Policy
```bash
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": {
                "AWS": "arn:aws:iam::664695030410:user/root"
            },
            "Action": [
                "s3:GetObject",
                "s3:PutObject",
                "s3:PutObjectAcl"
            ],
            "Resource": [
                "arn:aws:s3:::documents-kiwony/*"
            ]
        }
    ]
}
```

S3 -> Permissions -> Access Control List -> Acess for other AWS accounts
Add Requestor's canonical ID and give list permissions.



