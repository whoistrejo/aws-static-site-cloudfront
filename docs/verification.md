# Verification

After apply, upload the sample site:
```bash
aws s3 sync ../site "s3://$(terraform output -raw bucket_name)" --delete
curl -I "$(terraform output -raw cloudfront_url)"
```
Expected: HTTPS response with a successful status after CloudFront finishes deploying. S3 objects should not be publicly readable. Verify the bucket public-access block and CloudFront OAC in the AWS console.
