AWS CloudFormation Template: Codepipeline S3 Bucket and CloudFront Distribution
Overview:
    This CloudFormation template creates an S3 bucket named "recipto-demo-bucket" and a CloudFront distribution. The CloudFront distribution is configured to use the S3 bucket as its origin and enforces HTTPS redirection for enhanced security.
Resources:
     1.S3 Bucket (MyS3Bucket):
        Bucket Name: recipto-demo-bucket
    2.CloudFront Distribution (MyCloudFrontDistribution):
        1.Origins:
            1.Domain Name: !GetAtt MyS3Bucket.DomainName
            2.ID: S3Origin
            3.S3 Origin Config:
                Origin Access Identity: (blank)
            4.Default Cache Behavior:
                1.Target Origin ID: S3Origin
                2.Forwarded Values:
                     1.Query String: 'false'
                     2.Cookies:
                         1.Forward: none
            5.Viewer Protocol Policy: redirect-to-https
            6.Allowed Methods: GET, HEAD
            7.Cached Methods: GET, HEAD
            8.Default TTL: 86400 seconds (24 hours)
            9.Min TTL: 0 seconds
            10.Max TTL: 31536000 seconds (1 year)
            11.Enabled: true
Usage:
    1. Deploy this CloudFormation template on AWS.
    2. After deployment, you will have an S3 bucket named "recipto-demo-bucket" and a CloudFront distribution configured with the S3 bucket as its origin.
    3. The CloudFront distribution enforces HTTPS redirection and has caching settings specified.
