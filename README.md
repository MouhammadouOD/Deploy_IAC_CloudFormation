### Project Title - Deploy a high-availability web app using CloudFormation
This folder provides the complete code for a high-availability web app Deployment using CloudFormation. This folder contains the following files:


#### network.yml
This YAML template contain the cloudformation code for the cloud infrastructure, as required for the project such as VPC, Subnets, InternetGateway, RouteTables, Routes, NatGateways, NatEIP, etc. 

#### network.json
This JSON file contains all parameters needed in the network.yml
the `${EnvironmentName}` would be substituted with `IacProject`

#### create.sh & update.sh
These scripts are used to create and update our stack.

#### Note: 
deploy the network infrastructure first before launching the resources stack

#### command:
    ./create.sh IacProject network.yml network.json

#### resources.
This YAML file provides all necessary ressources to deploy a high-availabilty web app 
in the network that we have just created. It provides SecurityGroups, LaunchConfiguration, AutoScalingGroup, TargetGroup with HealthCheck, LoadBalancer, Listener, ListenerRule, S3 bucket, IAMRole and IAMProfile to provide ec2 access to the S3 bucket,
JumpBox(server with which we'll connect to our ec2instances placed in private subnets)

#### Info
    - We provided the loadbancer DNSName as an output
    - Don't forget to change MyIp paramater value to your Personal Ip Address

#### command
    ./create.sh IacProjectResources resources.yml resources.json