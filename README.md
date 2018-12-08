# Aws Cloudformation Active Directory

Setup an Active Directory for a Microsoft Server that will be deployed at Aws Cloudformation.

# Install the AWS CLI

pip install awscli.

Obs.: Pip is tool for installing Python packages.

# Create a file with yaml extension
## Struncture of the file
example.yaml
```yaml
  AWSTemplateFormatVersion: "version date"
  Description:
    String

  Metadata:
    template metadata

  Parameters:
    set of parameters

  Mappings:
    set of mappings

  Conditions:
    set of conditions

  Transform:
    set of transforms

  Resources:
    set of resources

  Outputs:
    set of outputs
```

**Format Version (optional)**

  _The AWS CloudFormation template version that the template conforms to. The template format version is not the same as the API or WSDL version. The template format version can change independently of the API and WSDL versions._

**Description (optional)**

  _A text string that describes the template. This section must always follow the template format version section._

**Metadata (optional)**

  _Objects that provide additional information about the template._

**Parameters (optional)**

  _Values to pass to your template at runtime (when you create or update a stack). You can refer to parameters from the Resources and Outputs sections of the template._

**Mappings (optional)**

  _A mapping of keys and associated values that you can use to specify conditional parameter values, similar to a lookup table. You can match a key to a corresponding value by using the Fn::FindInMap intrinsic function in the Resources and Outputs section._

**Conditions (optional)**

  _Conditions that control whether certain resources are created or whether certain resource properties are assigned a value during stack creation or update. For example, you could conditionally create a resource that depends on whether the stack is for a production or test environment._

**Transform (optional)**

  _For serverless applications (also referred to as Lambda-based applications), specifies the version of the AWS Serverless Application Model (AWS SAM) to use. When you specify a transform, you can use AWS SAM syntax to declare resources in your template. The model defines the syntax that you can use and how it is processed._

  _You can also use AWS::Include transforms to work with template snippets that are stored separately from the main AWS CloudFormation template. You can store your snippet files in an Amazon S3 bucket and then reuse the functions across multiple templates._

**Resources (required)**

  _Specifies the stack resources and their properties, such as an Amazon Elastic Compute Cloud instance or an Amazon Simple Storage Service bucket. You can refer to resources in the Resources and Outputs sections of the template._

**Outputs (optional)**

  _Describes the values that are returned whenever you view your stack's properties. For example, you can declare an output for an S3 bucket name and then call the aws cloudformation describe-stacks AWS CLI command to view the name._
