
aws route53 list-hosted-zones --profile aep-aries --query "HostedZones[].[Name,Id,Config.PrivateZone]" --output table
