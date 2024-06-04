# S3 Bucket with CloudTrail, Logging, and Event Notifications

This AWS CloudFormation template creates an S3 bucket with various features, including server access logging, lifecycle rules, CloudTrail data events, and event notifications.

## Features

- **S3 Bucket**: Creates an S3 bucket with the specified name.
- **Server-side Encryption**: Enables server-side encryption with Amazon S3 managed keys (SSE-S3) for the S3 bucket.
- **Bucket Versioning**: Optionally enables or disables versioning for the S3 bucket based on a user-defined parameter.
- **Access Logging**: Configures access logging for the S3 bucket, storing the logs in a separate log bucket.
- **Lifecycle Rules**: Transitions objects to the STANDARD_IA storage class after a specified number of days.
- **Event Notifications**: Sends notifications to an SNS topic when objects with a specific suffix (e.g., `.jpg`) are created in the S3 bucket.
- **CloudTrail Data Events**: Configures CloudTrail to log data events for the S3 bucket.

## Parameters

The CloudFormation template accepts the following parameters:

- `S3BucketName` (Required): The name of the S3 bucket to create.
- `BucketLogsPrefix` (Optional, default: `logs/`): The prefix for log files in the log bucket.
- `LifecycleTransitionDays` (Optional, default: `30`): The number of days after object creation to transition to the STANDARD_IA storage class.
- `NotificationEventSuffix` (Optional, default: `.jpg`): The suffix for object keys to trigger event notifications.
- `AccountId` (Optional, default: `xxxxxxx`): The AWS Account ID that needs access to publish to the SNS topic.
- `Email` (Optional, default: `xxxxxxx.com`): The email address to receive SNS notifications.
- `BucketVersioningEnabled` (Optional, default: `Disable`): Enable or disable versioning for the S3 bucket.

## Outputs

The CloudFormation template outputs the following values:

- `S3BucketName`: The name of the created S3 bucket.
- `LogBucketName`: The name of the log bucket used for access logging.
- `SNSTopicArn`: The ARN of the SNS topic used for event notifications.

## Usage

1. Deploy the CloudFormation template using the AWS Management Console, AWS CLI, or other deployment methods.
2. Provide the required parameters during the deployment process.
3. After successful deployment, the S3 bucket and associated resources will be created.
4. Use the outputs to identify the created resources (e.g., S3 bucket name, log bucket name, SNS topic ARN).

## Notes

- The CloudFormation template assumes the existence of an AWS account and the necessary permissions to create the specified resources.
- Modify the default parameter values (e.g., `AccountId`, `Email`) according to your specific requirements.
- Review and customize the resource configurations (e.g., lifecycle rules, notification filters) as needed.
