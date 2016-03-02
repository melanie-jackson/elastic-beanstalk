# Deep Security for AWS Elastic Beanstalk

Scripts to deploy and activate the Deep Security agent via [AWS Elastic Beanstalk](https://aws.amazon.com/elasticbeanstalk/).

## Usage

To integrate Deep Security Agent into the AWS Elastic Beanstalk configuration:

1. Edit the Deep Security Agent AWS Elastic Beanstalk extension configuration file for your operating system to provide your tenant ID, tenant password, and the policy ID for use when activating the Agent.
1. Add the configuration file to the ```.ebextensions``` directory of your source bundle.
1. Re-deploy your application and your servers will automatically download the latest Agent and activate into the list of instances on the Computers page in Deep Security. 

> Tip: To locate your tenant ID, password and policy ID, go to Support > Deployment Scripts to display the Deployment Script Generator. Generate a script, then copy the values from the script.