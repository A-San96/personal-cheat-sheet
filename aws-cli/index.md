# AWS CLI v2 Cheat sheet

## Execute AWS Lambda Function
> [Click here for more information](https://awscli.amazonaws.com/v2/documentation/api/latest/reference/lambda/invoke.html)
```
aws lambda invoke --function-name hello-world --invocation-type RequestResponse --log-type Tail --cli-binary-format raw-in-base64-out --region us-east-1 --payloa
d '{"name": "AWS Lambda"}' result.txt
```