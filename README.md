Thanks, Guru. aries.cloud.aep.com works well.

Entra ID: yes, it's for user login. Users sign in to ARIES with their AEP work accounts through Microsoft Entra ID. For that, we'll need an app registration in your Entra tenant, with the redirect URI https://aries.cloud.aep.com/ (we'll confirm the exact path), plus its client ID and a client secret, shared securely. Please also let us know which AEP groups should have access.

DNS: since ARIES sits behind an internal AWS load balancer, the record should be a Route 53 alias A record pointing to the load balancer, rather than a fixed IP (the load balancer's IPs can change). We can create it with our Terraform once the load balancer is deployed. Could you confirm the cloud.aep.com hosted zone is in this account (387340471575), and whether it's a private hosted zone?
