1. Check the load balancer's outputs

The record needs the load balancer's DNS name and zone ID:

cmd
cd C:\terraform\aries-terraform-aep\aries-terraform-aep\modules\alb
findstr /n "output resource" outputs.tf main.tf
Note the name of the resource "aws_lb" "…" line (for example "this" or "main")
Check whether an output like alb_zone_id exists. If it doesn't, add this at the end of modules\alb\outputs.tf (replace this with the real name):
hcl
output "alb_zone_id" {
  value = aws_lb.this.zone_id
}
2. Add two variables

At the end of environments\dev\variables.tf:

hcl
variable "route53_zone_id" {
  description = "Existing public hosted zone cloud.aep.com"
  type        = string
}

variable "app_hostname" {
  description = "ARIES hostname, e.g. aries.cloud.aep.com"
  type        = string
}
3. Add the record

At the end of environments\dev\main.tf:

hcl
########################################
# DNS – aries.cloud.aep.com -> internal ALB
########################################
data "aws_route53_zone" "app" {
  zone_id = var.route53_zone_id
}

resource "aws_route53_record" "app" {
  zone_id = data.aws_route53_zone.app.zone_id
  name    = var.app_hostname
  type    = "A"

  alias {
    name                   = module.alb.alb_dns_name
    zone_id                = module.alb.alb_zone_id
    evaluate_target_health = true
  }
}
4. Add the values to aep.tfvars
hcl
route53_zone_id = "Z07331021PJL72XPRQ45K" # cloud.aep.com (public)
app_hostname    = "aries.cloud.aep.com"
app_url         = "https://aries.cloud.aep.com"

(app_url already exists in the file: change that line, don't add a second one.)

5. Check and plan
cmd
cd C:\terraform\aries-terraform-aep\aries-terraform-aep\environments\dev
terraform fmt -recursive ..\..
terraform validate



You can do it with a few commands in cmd. Since app_url already exists in the file, that line must be replaced (not added a second time, which Terraform would reject).

cmd
cd C:\terraform\aries-terraform-aep\aries-terraform-aep\environments\dev
copy aep.tfvars aep.tfvars.bak

1. Remove the old app_url line:

cmd
findstr /v /b "app_url" aep.tfvars > aep.new
move /y aep.new aep.tfvars

2. Add the three lines at the end:

cmd
echo.>> aep.tfvars
echo route53_zone_id = "Z07331021PJL72XPRQ45K">> aep.tfvars
echo app_hostname    = "aries.cloud.aep.com">> aep.tfvars
echo app_url         = "https://aries.cloud.aep.com">> aep.tfvars

(Type them exactly as shown: no space before >>, so no extra spaces end up in the file.)

3. Check the result:

cmd
findstr /n "route53_zone_id app_hostname app_url" aep.tfvars

You should see each name once, with the new values.

If something looks wrong, restore the backup and try again:

cmd
copy /y aep.tfvars.bak aep.tfvars

Alternatively, Notepad is just as quick: notepad aep.tfvars → find the app_url line and change it → paste or type the two new lines at the end → Save.
terraform plan -var-file=aep.tfvars -out=aep.tfplan

Expected: Success! The configuration is valid, and the plan now includes aws_route53_record.app
