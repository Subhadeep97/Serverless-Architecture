1. S3 Bucket Setup
    Open your browser (Safari/Chrome) on MacBook Air and log in to the AWS Console.
    Search for "S3" and open the S3 dashboard.
    Click Create bucket and follow the prompts to create a new bucket (you can accept most defaults).
    Upload multiple files to this bucket.
    If you need files older than 30 days for testing:
    You can manually set the file’s "Last Modified" date only programmatically (since direct upload won’t change it), or use files you know are old (from backups, etc.).
    Otherwise, upload any files. The function will simply keep those newer than 30 days.

2. Create Lambda IAM Role
    Go to the IAM dashboard.
    Select Roles > Create role.
    Choose AWS Service and then Lambda.
    Click Next.
    Attach the AmazonS3FullAccess policy.
    Click Next twice, name your role (subhadeepLambdaS3CleanupRole), and create it.

3. Create Lambda Function
    Go to the Lambda dashboard.
    Click Create function.
    Choose Author from scratch.
    Name your function (S3CleanupFunction).
    Runtime: Python 3.13.
    Execution role: choose the IAM role you created (subhadeepLambdaS3CleanupRole).
    Click Create function.

4. Add Python (Boto3) Script to Lambda
    In the Lambda function editor, replace the default code with your code
    Click Deploy after pasting the code.

5. Manual Invocation and Verification
    On your Lambda function’s page, click Test.
    You may need to configure a simple test event (can be an empty object {}).
    Click Test to execute.
    View the function’s output and logs to see which files were deleted.
    Go to the S3 bucket and confirm that:
        Files older than 30 days have been deleted.
        Files newer than 30 days remain.
