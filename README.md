findstr /v /c:"ARIES_INTERNAL_HOSTNAME" aep.tfvars > aep.new
move /y aep.new aep.tfvars

findstr /n "route53_zone_id app_hostname app_url" aep.tfvars
