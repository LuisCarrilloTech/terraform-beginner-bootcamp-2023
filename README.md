# Terraform Beginner Bootcamp 2023

## Semantic Versioning :mage:

This project utilizes semantic versioning for its tagging. 

[Semantic Versioning - semver.org](https://semver.org/)

Given a version number MAJOR.MINOR.PATCH, increment the:

**MAJOR** version when you make incompatible API changes
**MINOR** version when you add functionality in a backward compatible manner
**PATCH** version when you make backward compatible bug fixes

Additional labels for pre-release and build metadata are available as extensions to the MAJOR.MINOR.PATCH format.

## Install Terraform CLI:

## Considerations with the Terraform CLI changes
The Terraform CLI installation instructions have changed due to gpg keyring changes. So we needed refer to the latest install CLI instructions via terraform Documentation and change the scripting for install. 

[Terraform installation guide:](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli)

## Refactoring into Bash Scripts

While fixing the Terraform CLI gpg deprecation issues we noticed that bash script steps were a considerable amount more code. So we decided to create a bash script to install the Terraform CLI.

This bash script is located here: [./bin/install_terraform_cli](./bin/install_terraform_cli.sh)
- This will keep the Gitpod task file tidy [.gitpod.yml](.gitpod.yml).
- This allows us an easier to debug the execute manually terraform CLI install
- This will allow better portability for other products that need to install terraform CLI.

## Working with ENV Vars

We can list out all environment variables using the `env` command

We can filter specific env vars using grep eg. `env | grep AWS_`

#### Setting and Un-setting Env Vars

In the terminal we can set using `export HELLO='world'`

In the terminal we unset using `unset HELLO`

We can set an env var temporarily when just running a command

```sh
HELLO='world' ./bin/print_message
```
Within a bash script we can set env without writing export eg.

```sh
#! /usr/bin/env bash

HELLO='world'

echo $HELLO
```

## Printing VARS

We can print an env var using echo eg. `echo $HELLO`

#### Scoping of ENV Vars

When you open up new bash terminals in VSCode it will not be aware of env vars in another windows. If you want env vars to persist across all future bash terminals that are open you need to set env vars in your bash profile. eg. `.bash_profile`

#### Persisting ENV Vars in Gitpod

We can persist env vars into gitpod by storing them in Gitpod Secrets Storage.

```sh
gp evn HELLO='world'
```
All future workspaces launched will set the env vars for all bash terminals opened in those workspaces.

You can also set env vars in the `.gitpod.yml` but this can only contain non-sensitive env vars.

### AWS CLI Installation for this project. 

AWS CLI is installed for the project via the bash script [`./bin/install_aws_cli`](./bin/install_aws_cli)

[Getting Started Install (AWS CLI)](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)

[How to configure AWS ENV Variables](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-envvars.html)
We can check if our AWS credentials is configured correctly by running the following AWS CLI command: 

```sh
aws sts get-caller-identity
```