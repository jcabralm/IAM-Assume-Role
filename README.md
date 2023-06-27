# IAM-Assume-Role.



To provide access to AWS services like Amazon S3 or Amazon EC2 to a user without any permissions, you can leverage the "AssumeRole" functionality in AWS Identity and Access Management (IAM). This allows the user to assume a role that has the necessary permissions to access the desired services. Here's the process:

1. Create a user in your AWS account without any permissions assigned. This user will act as the entity assuming the role to access AWS resources in another account.

2. Create a role in the target AWS account (the account where the resources reside) that will grant the necessary permissions. When creating the role, define a trust policy specifying the trusted entity as the IAM user in your AWS account. Add the following "Principal" section to the trust policy:

    "Principal": {
    "AWS": "arn:aws:iam::YOUR_ACCOUNT_ID:user/USERNAME"
    }

    Replace "YOUR_ACCOUNT_ID" with your AWS account ID and "USERNAME" with the name of the IAM user you created in step 1.

    Optional: If you require additional permissions for the role, you can also attach additional policies to it to grant specific access.

1. Connect to the AWS Management Console using the IAM user you created in step 1, ensuring you are in the AWS account where the user is located.

2. In the AWS Management Console, navigate to the "Switch Role" functionality. Enter the following information:

    Account: Enter the account number of the target AWS account where the role is defined.
    Role: Specify the name of the role you created in the target account.
    Display name: Provide a name that will be displayed to identify the role. For example, you can use "devopsjack" as the display name.

    Once you have successfully connected using the "Switch Role" functionality, you will have access to the AWS resources within the target account based     on the permissions assigned to the role.
