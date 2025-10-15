# Generate key pair
```sh
aws ec2 create-key-pair --key-name max-app-key --query 'KeyMaterial' --output text > max-app-key.pem
chmod 400 max-app-key.pem
```
# Deploy the cloudformation template
```sh
aws cloudformation deploy --template-file infra/max-app.yml --stack-name MaxInfra --capabilities CAPABILITY_IAM --parameter-overrides KeyName=max-app-key InstanceType=t2.micro AppName=max-app HtmlContent=$HTML_CONTENT BuildId=$TIMESTAMP
```
