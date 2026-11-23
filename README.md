aws ec2 describe-route-tables --profile aep-aries --region us-east-2 --filters Name=vpc-id,Values=vpc-0a5c1a4507b784997 --query "RouteTables[].[Associations[].SubnetId,Routes[].[DestinationCidrBlock,TransitGatewayId,GatewayId,NatGatewayId]]" --output text
\terraform>aws ec2 describe-route-tables --profile aep-aries --region us-east-2 --filters Name=vpc-id,Values=vpc-0a5c1a4507b784997 --query "RouteTables[].[Associations[].SubnetId,Routes[].[DestinationCidrBlock,TransitGatewayId,GatewayId,NatGatewayId]]" --output text
10.203.3.0/24   None    local   None
100.64.0.0/16   None    local   None
subnet-0aa71c6a26d6dd63c        subnet-02eefe783fd4e7004        subnet-0fb03cebcc2514d80
10.203.3.0/24   None    local   None
100.64.0.0/16   None    local   None
0.0.0.0/0       tgw-02ac34f9cf5cc3667   None    None
10.203.3.0/24   None    local   None
100.64.0.0/16   None    local   None
10.0.0.0/8      tgw-02ac34f9cf5cc3667   None    None
0.0.0.0/0       tgw-02ac34f9cf5cc3667   None    None
None    None    vpce-0aa45a822e8bebefb  None


C:\terraform>
