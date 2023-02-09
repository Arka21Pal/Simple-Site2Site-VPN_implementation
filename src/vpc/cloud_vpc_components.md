# For AWS VPC, in the cloud


Adrian uses:

- `awsVPC` - `AWS::EC2::VPC`
- `awsSnPrivateA` - `AWS::EC2::Subnet`
- `awsSnPrivateB` - `AWS::EC2::Subnet`
- `awsRTCustom` - `AWS::EC2::RouteTable`
- `awsRTAssociationPrivateA` - `AWS::EC2::SubnetRouteTableAssociation`
- `awsRTAssociationPrivateB` - `AWS::EC2::SubnetRouteTableAssociation`
- `awsSG`: `AWS::EC2::SecurityGroup`
- `awsSGSelfReference`: `AWS::EC2::SecurityGroupIngress`
- `awsEC2Role`: `AWS::IAM::Role`
- `awsEC2InstanceProfile`: `AWS::IAM::InstanceProfile`
- `awsVPCeSSM`: `AWS::EC2::VPCEndpoint`
- `awsVPCeSSMEC2Messages`: `AWS::EC2::VPCEndpoint`
- `awsVPCeSSMMessages`: `AWS::EC2::VPCEndpoint`
- `awsVPCeS3`: `AWS::EC2::VPCEndpoint`
- `awsVPCeCloudFormation`: `AWS::EC2::VPCEndpoint`
    - https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-ec2-vpcendpoint.html
- `awsENIServerPrivateA`: `AWS::EC2::NetworkInterface`

A session manager (SSM) is important since it allows one to manage servers without SSH, with just an authentication based workload.

An Internet Gateway lets the VPC access the internet. I wonder why Adrian left it and how he still got it working.

Answer: He asks us to use a VGW (Virtual Private Gateway) in the first Stage, instead of an IGW. Link: https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-ec2-vpngateway.html

Also asks us to create a GGW (Customer Gateway) for the Customer Router (custom OPNsense router in my case) to connect to the internet and the VPN.
