Step-by-Step Guide: Automated EC2 Instance Management with AWS Lambda and Boto3

1. Setup: Create EC2 Instances and Apply Tags

A. Log In and Navigate to EC2
  Open Safari or another browser on your MacBook Air.
  Go to the AWS Management Console and log in.

B. Launch Two EC2 Instances
  In the AWS Console, search "EC2" and open the EC2 Dashboard.
  Click "Launch instances".
  Choose the Amazon Linux 2 AMI or any other suitable AMI.
  Select t2.micro as the instance type.
  Click Next: Configure Instance Details.
  Continue through the steps > Add Tags.

C. Tag the Instances
  For the first instance:
  Set Tag Key to: Action
  Set Tag Value to: Auto-Stop
  For the second instance:
  Set Tag Key to: Action
  Set Tag Value to: Auto-Start
  Review and launch both instances.

2. Create IAM Role for Lambda
A. Open IAM Dashboard
  Search for "IAM" in AWS Management Console.

B. Create New Role
  Click Roles > Create role.
  Choose type: AWS service.
  Select Lambda.
  Click Next.

C. Attach Permission Policy
  Search for and add the policy: AmazonEC2FullAccess.
  Click Next: Tags (optional).
  Click Next: Review.
  Give the role a name (my role - LambdaEC2ManagementRole).
  Click Create role.

3. Create Lambda Function
A. Open Lambda Dashboard
    Search for "Lambda" in AWS Management Console.

B. Create New Function
  Click Create function.
  Choose Author from scratch.
  Name: ManageEC2Instances.
  Runtime: Python 3.13 (choose latest available).
  Under 'Execution role', select Use an existing role and pick the IAM role you just created.
  Click Create function.

4. Add Boto3 Script to Lambda
   Steps:
   Scroll to the Function code section in the Lambda configuration panel.
   Replace the default code with your code.
   Click Deploy to save.

5. Manual Lambda Invocation and Verification
A. Test the Lambda Function
  On your Lambda’s page, click Test.
  Name your test event (input can be empty for this use case).
  Click Test.

B. Verify Instance State Changes
  Go back to the EC2 dashboard.
  Refresh the Instances panel.
  Confirm that:
  The instance tagged Auto-Stop is stopped.
  The instance tagged Auto-Start is running.
   
