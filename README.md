mkdir C:\Tools\crane
move %USERPROFILE%\Downloads\go-containerregistry_Windows_x86_64.tar.gz C:\Tools\crane\
cd C:\Tools\crane
tar -xzf go-containerregistry_Windows_x86_64.tar.gz
set PATH=%PATH%;C:\Tools\crane
crane version



certutil -hashfile <path>\oi-aries-api.tar SHA256
certutil -hashfile <path>\oi-aries-fe.tar SHA256

Sign crane in to ECR (no token copying)
for /f %t in ('aws ecr get-login-password --region us-east-2 --profile aep-aries') do crane auth login 387340471575.dkr.ecr.us-east-2.amazonaws.com -u AWS -p %t

5. Push the two images
6. 
for /f %t in ('aws ecr get-login-password --region us-east-2 --profile aep-aries') do crane auth login 387340471575.dkr.ecr.us-east-2.amazonaws.com -u AWS -p %t

crane push <path>\oi-aries-fe.tar 387340471575.dkr.ecr.us-east-2.amazonaws.com/aep-demo-aries-fe:20261124-279502-fe

aws ecr describe-images --repository-name aep-demo-aries-api --region us-east-2 --profile aep-aries --query "imageDetails[].imageTags" --output table
aws ecr describe-images --repository-name aep-demo-aries-fe --region us-east-2 --profile aep-aries --query "imageDetails[].imageTags" --output table



aws ecr describe-repositories --region us-east-2 --profile aep-aries --query "repositories[].repositoryUri" --output table
