# awsAppLB_CLI
This repo contains steps for the creation of Application Load Balancer


Step1 : Create the required number of EC2 Instance
--------------------------------------------------
Step2 :  CREATING A LOAD BALANCER
-----------------------------------
From the CLI trigger the below commands 

Inputs to the CLI-> Subnets Details  and Security Group Details

SYNTAX→ aws elbv2 create-load-balancer --name <LOAD BALANCER NAME> --subnets <SUBNET ID OF INSTANCE 1> <SUBNET ID OF INSTANCE 2> --security-groups <SECURITY GROUP ID>

Step3 : Create n Target Groups
----------------------------
Inputs to the CLI-> VPC ID

SYNTAX→ aws elbv2 create-target-group --name <TARGET GROUP NAME> --protocol HTTP --port 80 --vpc-id <VPC ID>
  
  

Step4 : Register the Targets with their Respective Target groups
-----------------------------------------------------------------
Inputs to the CLI-> TARGET GROUP ARN and Instance ID

SYNTAX→ aws elbv2 register-targets --target-group-arn <TARGET GROUP ARN> --targets Id=<INSTANCE ID>


Step5 : Creating Listener Default Rules
----------------------------------------

Inputs to the CLI -> LOAD BALANCER ARN. and Target Groups ARN

SYNTAX→ aws elbv2 create-listener --load-balancer-arn <LOAD BALANCER ARN> --protocol HTTP --port 80 --default-actions Type=forward,TargetGroupArn=<TARGET GROUP ARN>


Step 6: Creating Listeners for other rules
------------------------------------------

Inputs to the CLI -> LISTENER ARN and TARGET GROUP ARN

SYNTAX→ aws elbv2 create-rule --listener-arn <LISTENER ARN>--priority 10 --conditions Field=path-pattern,Values='/images/*' --actions Type=forward,TargetGroupArn=<TARGET GROUP ARN>
  
  
Steps 7: Verifying the health of the Target Groups
--------------------------------------------------

Inputs : TARGET GROUP ARN

SYNTAX→ aws elbv2 describe-target-health --target-group-arn <TARGET GROUP ARN>










