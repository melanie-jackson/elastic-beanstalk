# Deep Security for AWS Elastic Beanstalk

Scripts to deploy and activate the Deep Security agent via [AWS Elastic Beanstalk](https://aws.amazon.com/elasticbeanstalk/).

## Usage 

To integrate Deep Security Agent into the AWS Elastic Beanstalk configuration:

1. Edit the Deep Security Agent AWS Elastic Beanstalk extension configuration file for your operating system to match your Deep Security deployment
1. Add the configuration file to the ```.ebextensions``` directory of your source bundle.
1. Re-deploy your application and your servers will automatically download the latest Agent and activate into the list of instances on the Computers page in Deep Security. 

> Tip: To locate your tenant ID, password and policy ID, go to Support > Deployment Scripts to display the Deployment Script Generator. Generate a script, then copy the values from the script.

### Using The .ebextension With Deep Security as a Service

To configure the .ebextension for use with [Deep Security as a Service](https://app.deepsecurity.trendmicro.com/SignIn.screen), you will need to replace 3 items in the appropriate .ebextension. Each of these items is in the final command in the extension (the activation step for the Deep Security agent).

As seen in the [Amazon Linux extension](deep-security-as-a-service/99deepsecurity-as-a-service-amzn1-x86_64.config.ebextension#L9)

```command: '/opt/ds_agent/dsa_control -a dsm://agents.deepsecurity.trendmicro.com:443/ "tenantID:REPLACE-WITH-YOUR-TENANT-ID" "tenantPassword:REPLACE-WITH-YOUR-TENANT-PASSWORD" "policyid:REPLACE-WITH-YOUR-POLICY-ID" --max-dsm-retries 0 >/tmp/dsa_control.log 2>&1'```

1. ```"tenantID:**REPLACE-WITH-YOUR-TENANT-ID**"```
1. ```"tenantPassword:**REPLACE-WITH-YOUR-TENANT-PASSWORD**"```
1. ```"policyid:REPLACE-WITH-YOUR-POLICY-ID"```

You can find this information within the Deep Security Manager console under **Support > Deployment Scripts**. This dialog will allow you to create a customized deployment script that contains these values.

### Using The .ebextension With Deep Security

To configure the .ebextension for use with your own Deep Security deployment, you will need to replace 2 items in the appropriate .ebextension. These items is in the final command in the extension (the activation step for the Deep Security agent).

As seen in the [Amazon Linux extension](deep-security/99deepsecurity-amzn1-x86_64.config.ebextension#L9)

```command: '/opt/ds_agent/dsa_control -a dsm://REPACE-WITH-YOUR-DSM-IP:4120/ "policyid:REPLACE-WITH-YOUR-POLICY-ID" --max-dsm-retries 0 >/tmp/dsa_control.log 2>&1'```

1. ```dsm://**REPACE-WITH-YOUR-DSM-IP**:4120/```
1. ```"policyid:REPLACE-WITH-YOUR-POLICY-ID"```

You can find this information within the Deep Security Manager console under **Help > Deployment Scripts**. This dialog will allow you to create a customized deployment script that contains these values.