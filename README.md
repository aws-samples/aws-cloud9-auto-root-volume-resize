## AWS Cloud9 Automatic Root Volume Resizing

Cloud9 provides a consistent environment for development teams that allows for ease of development by easily integrating with AWS.  However, when launching a Cloud9 instance environment, no options are provided that will allow for adjusting the size of the root volume and the environment will launch using the default size of 10 GiB.  This limited size can prove cumbersome if teams start development work in the Cloud9 instance environment without realizing this storage space is limited without intervention.

This solution allows for a near-seamless integration with the existing Cloud9 instance environment launch process but utilizing an optional tag (“cloud9:root_volume_size”) to indicate the desired root volume size in GiB.  Additionally, modifying an existing Cloud9 instance environment to include or change this tag will also adjust the root volume size as desired.  These events are captured and directed to an SSM Automation runbook that will be responsible for executing the necessary scripts to resize the Cloud9 instance environment root volume.

## Usage

1. Clone the repository and identify the solution template in the `templates/` directory.  This template may be uploaded to S3 for use in the next step but it is not necessary.

2. Use the identified solution template to launch an AWS CloudFormation stack.  The solution is self-contained and has no necessary parameters to provide.

3. Launch a new or modify an existing Cloud9 instance environment, providing the specific tag key (“cloud9:root_volume_size” without quotes) and its value (the desired root volume size in GiB).  View the SSM Automation runbook execution in the SSM Management Console to verify as well as access the Cloud9 environment and validate the desired root volume size.

## Security

See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more information.

## License

This library is licensed under the MIT-0 License. See the LICENSE file.

