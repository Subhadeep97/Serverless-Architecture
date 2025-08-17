Step-by-Step Guide: Auto-Tagging EC2 Instances on Launch with AWS Lambda and Boto3:

1. EC2 Prerequisite
  Log in to the AWS Management Console from your PC.
  Verify you can launch EC2 instances in your AWS account.

2. Create Lambda IAM Role
  Go to the IAM dashboard.
  Click Roles → Create role.
  Choose AWS service → Lambda.
  Click Next.
  Attach the AmazonEC2FullAccess policy.
  Click Next twice, then give your role a name (my given Name - LambdaAutoTagEC2Role) and create the role.

3. Create the Lambda Function
  Go to the Lambda dashboard.
  Click Create function → Author from scratch.
  Name your function (My Given Name - AutoTagEC2Instance).
  Select Python 3.13 as the runtime.
  Choose the IAM role you created (LambdaAutoTagEC2Role).
  Click Create function.
  Paste code into the Lambda function editor.
  Click Deploy to save the Lambda function.

4. Create CloudWatch Event Rule to Trigger Lambda
  Go to the CloudWatch dashboard, then Events → Rules → Create rule.
  Event Source:
  Choose Event Pattern.
  Service Name: EC2
  Event Type: EC2 Instance State-change Notification
  Under “Specific state(s)”, select 'running' (to catch new instances).
  Target:
  Add target → Lambda function
  Choose your Lambda function (AutoTagEC2Instance)
  Click Configure details, name your rule, and enable it.

5. Testing the Automation
  Launch a new EC2 instance from the EC2 dashboard.
  Wait a few minutes for the function to be triggered (usually <1 minute).
  Navigate to EC2 dashboard → Instances.
  Select the newly launched instance → Tags tab. (** in this case i named my instance subhadeepAutoTagging1 **)
  Confirm: Your instance is automatically tagged with:
  LaunchDate (YYYY-MM-DD)
  The custom tag you specified (Owner: AutoTagged)


