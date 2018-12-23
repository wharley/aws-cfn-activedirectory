## Step 1

Created scripts folder with all ps1 and AWSQuickStart.zip


## Step 2

  - Created all files ps1 and your's  configurations
  - Created bucket from s3 on the aws
    - Name folder: stack-master
    - Include in the stack-master folder the subdirectory script and subModules
  - Uploaded all files to the s3-bucket stack-master/scripts

## Step 3

  - Created aws-vpc.yaml file
  - Uploaded to the s3 from stack-master/subMobules

## Step 4

  - Created ad-1.yaml file
  - Uploaded to the s3 from stack-mastaer/subModules

## Step 5

  - Created rdgw-domain.yaml file
  - Uploaded to the s3 from stack-master/subModule

## Step 6

  - Created ad-master.yaml stack file
  - Using templateUrl to import aws-vpc, ad-1 and rdgw-domain stacks
  - Deployed to the aws cloudformation

>  aws --region us-east-1 cloudformation deploy --template-file awsCloudformation/ad-master.yaml --stack-name ad-master --capabilities CAPABILITY_IAM  --parameter-overrides AvailabilityZones=value KeyPairName=value DomainAdminPassword=value RDGWCIDR=value
