# AWS CloudFormation Sample Templates
Use sample AWS CloudFormation templates to learn how to declare specific AWS resources or solve a particular use case. We recommend that you use sample templates as a starting point for creating your own templates, not for launching production-level environments. Before launching a template, always review the resources that it will create and the permissions it requires.

## Creating an AWS CloudFormation template from scratch involves several steps. Here is a general overview of the process:

**Identify the resources you need to create**: Determine the AWS resources that you want to create, such as EC2 instances, S3 buckets, or RDS databases.

**Define the template structure**: You can either define the template structure manually or use an AWS-provided template as a starting point. The structure should include the necessary metadata, such as the template format version, description, and list of resources.

**Define the resources**: For each resource, specify its type, properties, and any dependencies. For example, if you are creating an EC2 instance, you need to specify its instance type, AMI ID, security groups, and key pair.

**Define the resources**: If you want to make your template `more flexible and reusable`, you can add parameters and mappings. Parameters allow users to provide input values when they create a stack, while mappings provide a way to retrieve a value based on a key.

**Add conditions and outputs**: Conditions allow you to define logical statements that control whether a resource is created or not. Outputs allow you to expose certain values from the stack for other resources or users to access.

**Validate the template**: Before you deploy the template, you should validate it to ensure that it is well-formed and free of syntax errors. AWS provides a CloudFormation validation tool that you can use for this purpose.
```
cd ../
aws cloudformation validate-template --template-body file://S3.yaml
```
If the output indicates that your template has syntax or other errors, correct them, and then run the command again to verify that they have been resolved.

**Deploy the template**: Once you have validated the template, you can deploy it to create the desired AWS resources. You can use the AWS Management Console, CLI, or SDK to deploy the template.
```
aws configure get region
aws cloudformation create-stack --stack-name CreateBucket --template-body file://S3.yaml
```

**Test and refine**: After the stack is created, you should test it to ensure that it is functioning as expected. You can also refine the template based on feedback and requirements.
```
aws cloudformation update-stack --stack-name CreateBucket --template-body file://S3.yaml
```
Tip: Proper YAML syntax is important. If you receive a ValidationError when you run update-stack, review your use of colons and confirm that you indented each line appropriately. The example templates in the documentation provide a good reference for well-structured YAML templates.
Overall, creating a CloudFormation template from scratch can be complex, but it offers a powerful way to manage AWS resources as code.

## About the Repository
The AWS CloudFormation team and approved contributors provide and maintain sample templates in the `aws ` folder. 

We also collect and make available templates developed by the community. These sample templates are located in the `community` folder and its subfolders. We encourage your contributions to these templates. Note, however, that we don't test, maintain, or support community templates.

## Submitting Templates
Before you submit a template, we suggest that you follow these guidelines to help maintain consistency between templates.

- Test your template. Can you successfully create a stack with it? When you create a stack, AWS CloudFormation uses the `ValidateTemplate` API to check your template. When you delete a stack, is the stack (and all of its resources) successfully deleted? Make sure users aren't left with stray resources or stacks that have deletion errors.
- In the Description section, add a brief description of your template. The description should indicate what the template does and why it's useful. For example:
 ```Description: "Create a LAMP stack using a single EC2 instance and a local MySQL database for storage. This template demonstrates using the AWS CloudFormation bootstrap scripts to install the packages and files necessary to deploy the Apache web server, PHP, and MySQL when the instance is launched."```
- Format your template to make it human readable:
	- Err on the side of human readability. If it makes your template easier to read, do it.
	- Use a linter. There isn't one specific tool that we use. Whatever you use, make sure it also checks for syntax errors.
	- Consider using two-space indents to reduce line wrapping.
- Review IAM resources. If you include IAM resources, follow the standard security advice of granting least privilege (granting only the permissions required to do a task).
- Remove secrets/credentials from your template. You might hardcode credentials or secrets in your template when you're testing. Don't forget to remove them before submitting your template. You can use this tool to help you scrub secrets: [https://github.com/awslabs/git-secrets](https://github.com/awslabs/git-secrets).
- Add your template to the correct folder so that others can discover it. If your template demonstrates a particular service, add it to the Services folder. If it uses multiple services to address a particular use case, add it to the Solutions folder.

When your template is ready, submit a pull request. A member of the AWS organization will review your request and might suggest changes. We review templates to check for general security issues, but we won't test or maintain them. If we don't get back to you within a week of your submission, use your pull request to send us a message.

## Additional Resources
In the *AWS CloudFormation User Guide*, you can view more information about the following topics:

- Learn how to use templates to create AWS CloudFormation stacks using the [AWS Management Console](http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-console-create-stack.html) or [AWS Command Line Interface (AWS CLI)](http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-cli-creating-stack.html).
- To view all the supported AWS resources and their properties, see the [Template Reference](http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/template-reference.html).
