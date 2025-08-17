Here’s a complete, step-by-step breakdown to automate the detection of S3 buckets missing server-side encryption using Lambda and Boto3:

1. S3 Bucket Setup
  Log in to your AWS Console.
  Navigate to the S3 dashboard.
  Create several buckets:
  For some, leave server-side encryption disabled.
  For others, enable encryption while creating or editing bucket settings (under “Default encryption”).

** i have created 4 buckets. ue-bucket1, ue-bucket2, ue-bucket3 & ue-bucket4 **

2. Lambda IAM Role
  Go to the IAM dashboard.
  Click Roles > Create role.
  Select AWS Service → Lambda.
  Click Next.
  Attach policy: Search and attach AmazonS3ReadOnlyAccess.
  Proceed, name the role (My Role - LambdaS3MonitorRole), and create it.

3. Create Lambda Function
  Go to the Lambda dashboard.
  Click Create function.
  Select Author from scratch.
  Enter a name (e.g., UnencryptedS3BucketsMonitor).
  Choose Python 3.x runtime.
  Assign the IAM role you just created (LambdaS3MonitorRole).
  Click Create function.

4. Add Boto3 Python Script
  Paste the code script in the Function code editor.
  Click Deploy to save your function.

5. Manual Invocation & Review Results
  On the Lambda function page, click Test.
  Create a simple test event (leave the event data as {}).
  Click Test to execute the function.

** in case the test fails and shows error in timeout, you need to increase the lambda timeout settings 
   by going to the configuration tab > general configuration > edit > set timeout to bigger values (1 - 2 minutes)**

