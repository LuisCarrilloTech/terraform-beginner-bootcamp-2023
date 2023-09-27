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
The Terraform CLI installation instructions have changed due to gpg keyring changes. So we needed refer to the latest install CLI instructions via terraform Doucmentioation and change the scripting for install. 

[Terraform installation guide:](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli)

## Refactoring into Bash Scripts

While fixing the Terraform CLI gpg deprecation issues we noticed that bash script steps were a considerable amount more code. So we decided to create a bash script to install the Terraform CLI.

This bash script is located here: [./bin/install_terraform_cli](./bin/install_terraform_cli.sh)
- This will keep the Gitpod task file tidy [.gitpod.yml](.gitpod.yml).
- This allows us an easier to debug the execute manually terraform CLI install
- This will allow better portability for other products that need to install terraform CLI.
