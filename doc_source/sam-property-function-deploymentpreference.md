# DeploymentPreference<a name="sam-property-function-deploymentpreference"></a>

Specifies the configurations to enable gradual Lambda deployments\. For more information about configuring gradual Lambda deployments, see [Deploying Serverless Applications Gradually](automating-updates-to-serverless-apps.md)\.

**Note**: You must specify an `AutoPublishAlias` in your [AWS::Serverless::Function](sam-resource-function.md) to use a `DeploymentPreference` object, otherwise an error will result\.

## Syntax<a name="sam-property-function-deploymentpreference-syntax"></a>

To declare this entity in your AWS SAM template, use the following syntax:

### YAML<a name="sam-property-function-deploymentpreference-syntax.yaml"></a>

```
  [Alarms](#sam-function-deploymentpreference-alarms): List
  [Enabled](#sam-function-deploymentpreference-enabled): Boolean
  [Hooks](#sam-function-deploymentpreference-hooks): [Hooks](sam-property-function-hooks.md)
  [Role](#sam-function-deploymentpreference-role): String
  [Type](#sam-function-deploymentpreference-type): String
```

## Properties<a name="sam-property-function-deploymentpreference-properties"></a>

 `Alarms`   <a name="sam-function-deploymentpreference-alarms"></a>
A list of CloudWatch alarms that you want to be triggered by any errors raised by the deployment\.  
*Type*: List  
*Required*: No  
*CloudFormation Compatibility*: This property is unique to AWS SAM and does not have an AWS CloudFormation equivalent\.

 `Enabled`   <a name="sam-function-deploymentpreference-enabled"></a>
Whether this deployment preference is enabled\.  
*Type*: Boolean  
*Required*: No  
*Default*: True  
*CloudFormation Compatibility*: This property is unique to AWS SAM and does not have an AWS CloudFormation equivalent\.

 `Hooks`   <a name="sam-function-deploymentpreference-hooks"></a>
Validation Lambda functions that are run before and after traffic shifting\.  
*Type*: [Hooks](sam-property-function-hooks.md)  
*Required*: No  
*CloudFormation Compatibility*: This property is unique to AWS SAM and does not have an AWS CloudFormation equivalent\.

 `Role`   <a name="sam-function-deploymentpreference-role"></a>
An IAM role ARN that CodeDeploy will use for traffic shifting\. An IAM role will not be created if this is provided\.  
*Type*: String  
*Required*: No  
*CloudFormation Compatibility*: This property is unique to AWS SAM and does not have an AWS CloudFormation equivalent\.

 `Type`   <a name="sam-function-deploymentpreference-type"></a>
There are two categories of deployment types at the moment: Linear and Canary\. For more information about available deployment types see [Deploying Serverless Applications Gradually](automating-updates-to-serverless-apps.md)\.  
*Type*: String  
*Required*: Yes  
*CloudFormation Compatibility*: This property is unique to AWS SAM and does not have an AWS CloudFormation equivalent\.

## Examples<a name="sam-property-function-deploymentpreference--examples"></a>

### DeploymentPreference<a name="sam-property-function-deploymentpreference--examples--deploymentpreference"></a>

Example deployment preference

#### YAML<a name="sam-property-function-deploymentpreference--examples--deploymentpreference--yaml"></a>

```
DeploymentPreference:
  Alarms:
  - Ref: AliasErrorMetricGreaterThanZeroAlarm
  - Ref: LatestVersionErrorMetricGreaterThanZeroAlarm
  Enabled: true
  Hooks:
    PostTraffic:
      Ref: PostTrafficLambdaFunction
    PreTraffic:
      Ref: PreTrafficLambdaFunction
  Type: Canary10Percent10Minutes
```