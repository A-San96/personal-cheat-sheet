<a href="../README.md">
<button>⬅Back</button>
</a>

# Serverless Framework cheat-sheet

## INSTALL
```bash
npm install -g serverless
```
## Configure serverless to use the AWS credentials

>  **NB:** In AWS don't forget to set up a new user in IAM named "serverless" and save the access key and secret key. By default give `AdministratorAccess` privilege.

```bash
sls config credentials --provider aws --key <YOUR_ACCESS_KEY> --secret <YOUR_SECRET_KEY> --profile serverless

```

## CREATE PROJECT
```bash
serverless create --template aws-nodejs-typescript --path <folder-name>
```

## INSTALL PLUGIN
```bash
npm install <plugin-name> --save-dev
```

## DEPLOY PROJECT
```bash
sls deploy -v
```