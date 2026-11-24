terraform plan -var-file=aep.tfvars -target=module.ecr -out=ecr.tfplan

terraform apply ecr.tfplan

mkdir %USERPROFILE%\crane

dir %USERPROFILE%\Downloads\*.tar.gz


move "%USERPROFILE%\Downloads\go-containerregistry_Windows_x86_64.tar.gz" "%USERPROFILE%\crane\"
cd %USERPROFILE%\crane
tar -xzf go-containerregistry_Windows_x86_64.tar.gz
set PATH=%PATH%;%USERPROFILE%\crane
crane version
