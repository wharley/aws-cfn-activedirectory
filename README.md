# Aws Cloudformation Active Directory

Setup an Active Directory for a Microsoft Server that will be deployed at Aws Cloudformation.

# Install the AWS CLI

pip install awscli.

Obs.: Pip is tool for installing Python packages.

# Create a file with yaml extension
## Struncture of the file
example.yaml
```
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
