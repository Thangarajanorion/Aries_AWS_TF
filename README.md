aws ec2 describe-route-tables --profile aep-aries --region us-east-2 --filters Name=vpc-id,Values=vpc-0bee26f8fe1b724b8 --query "RouteTables[].{table:RouteTableId,subnets:Associations[].SubnetId,dest:Routes[].DestinationCidrBlock,tgw:Routes[].TransitGatewayId}" --output json
[
    {
        "table": "rtb-0a6c50d12be3ba392",
        "subnets": [],
        "dest": [
            "10.203.0.0/24",
            "10.0.0.0/8",
            "0.0.0.0/0"
        ],
        "tgw": [
            "tgw-02ac34f9cf5cc3667",
            "tgw-02ac34f9cf5cc3667"
        ]
    },
    {
        "table": "rtb-012b48c42871a6359",
        "subnets": [],
        "dest": [
            "10.203.0.0/24",
            "0.0.0.0/0"
        ],
        "tgw": [
            "tgw-02ac34f9cf5cc3667"
        ]
    }
]


C:\terraform>aws ec2 describe-vpc-endpoints --profile aep-aries --region us-east-2 --filters Name=vpc-id,Values=vpc-0bee26f8fe1b724b8 --query "VpcEndpoints[].[ServiceName,VpcEndpointType,RouteTableIds]" --output text
com.amazonaws.us-east-2.s3      Gateway
rtb-0a6c50d12be3ba392


C:\terraform>
