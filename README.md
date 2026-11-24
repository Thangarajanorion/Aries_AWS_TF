set PATH=%PATH%;C:\terraform
set AWS_PROFILE=aep-aries
cd C:\terraform\aries-terraform-aep\aries-terraform-aep\environments\dev
terraform plan -var-file=aep.tfvars -target=module.ecr -out=ecr.tfplan
terraform apply ecr.tfplan

aws ecr describe-repositories --region us-east-2 --profile aep-aries --query "repositories[].repositoryName" --output table


for /f %t in ('aws ecr get-login-password --region us-east-2 --profile aep-aries') do crane auth login 387340471575.dkr.ecr.us-east-2.amazonaws.com -u AWS -p %t


crane push %USERPROFILE%\Downloads\oi-aries-fe.tar 387340471575.dkr.ecr.us-east-2.amazonaws.com/aep-demo-aries-fe:20261124-279502-fe


aws ecr describe-images --repository-name aep-demo-aries-api --region us-east-2 --profile aep-aries --query "imageDetails[].imageTags" --output table
aws ecr describe-images --repository-name aep-demo-aries-fe --region us-east-2 --profile aep-aries --query "imageDetails[].imageTags" --output table


set PATH=%PATH%;%USERPROFILE%\crane
