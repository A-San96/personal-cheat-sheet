# AWS CLI v2 Cheat sheet

## Execute AWS Lambda Function
> [Click here for more information](https://awscli.amazonaws.com/v2/documentation/api/latest/reference/lambda/invoke.html)
```bash
aws lambda invoke --function-name hello-world --invocation-type RequestResponse --log-type Tail --cli-binary-format raw-in-base64-out --region us-east-1 --payloa
d '{"name": "AWS Lambda"}' result.txt
```

## AWS S3
- Copy local folder to s3 bucket
```bash
aws s3 cp <my-folder> s3://<my-bucket-name>/<my-folder>/ --recursive
```