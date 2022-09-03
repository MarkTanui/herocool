# CREATING THE Heroku Clone AKA HeroCool

## Pulumi CLI
First, make sure you have the **Pulumi CLI** installed. The way to install is different depending on your operating system.
If you have MacsOS and Homebrew, you can use the command `brew install pulumi`.
If you have Windows and Chocolatey, you can use the command `choco install pulumi`.
[**This page will give you additional ways of installing Pulumi, ie: on linux.**](https://www.pulumi.com/docs/get-started/install/)

## AWS CLI
This project also uses AWS so you'll have to make sure you have an AWS account and have the CLI set up and authenticated.
You can sign up for a free AWS account [**here**](https://aws.amazon.com/free/)
Learn how to install the AWS CLI for your operating system [**here**](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)
For MacOS, you can use these commands:
```bash
curl "https://awscli.amazonaws.com/AWSCLIV2.pkg" -o "AWSCLIV2.pkg"
sudo installer -pkg AWSCLIV2.pkg -target /
```
For Windows there are a few extra steps and you should just [**follow the instructions here**](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-windows.html).
Next, you need to get an Access key ID and secret access key from AWS. [**Follow the instructions from Amazon to get these.**](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html#cli-configure-quickstart-creds)
Now run the following in the command line:
`aws configure`
Enter your Access Key ID and Secret Access Key when prompted. You can keep the "Default region name" and "Default output format" as None.

## Setup the Project
Clone this repo and access the directory:
```bash
git clone [repo]
cd herocool
pulumi new aws-python
```
A Pulumi project is just a directory with some files in it. It's possible for you to create a new one by hand. The `pulumi new` command, however, automates the process.
If this is the first time you have used Pulumi, you will be directed to enter an access code or login. To get an access code, go to **https://app.pulumi.com/account/tokens**
The pulumi new command allows you to choose between many templates. Choose the "aws-python" template. You can select the defaults for the other options.
This command will create all the files we need, initialized a new **stack** named ***dev*** (an instance of our project).
Every Pulumi program is deployed to a stack. A stack is an isolated, independently configurable instance of a Pulumi program. Stacks are commonly used to denote different phases of development. In this case, we called it '**dev**'.
Now we need to install two more dependencies for our project with
`venv/bin/pip install flask requests`

## Testing the App
Now it's time to try out the app. On the terminal, run this command:

```
FLASK_RUN_PORT=1337 FLASK_ENV=development FLASK_APP=__init__ PULUMI_ORG=[your-org-name] venv/bin/flask run
```
Now you can try out the app and create websites and VMs. **Make sure to delete them after creation so AWS does not keep charging you for the resources.**

## Conclusion
You should now know enough to start provisioning infrastructure in your own applications using Pulumi's automation API. 
If you experience a problem or notice a bug that you can solve, please do and make a pull request.
Also if you wish to establish contact: email - **themadbit@duck.com** or [**@themadbit**](https://twitter.com/themadbit)
