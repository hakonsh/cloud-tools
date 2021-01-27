# Cloud Tools

This repo contains and describes the tools you are expected to have installed and set up before embarking on the adventure that is working with infrastructure or deploying to the cloud.

The `terraform-wrapper` is a wrapper for Terraform. It's purpose is to:

- read values for secret variables from `pass`
- set up environment variables
- run custom commands (for example to dynamically generate more variables)
- run terraform passing along any arguments

# First time setup


## Install Terraform

Use the latest point release of Terraform 12 (change below)

```
brew install tfenv
tfenv install 0.12.20
```

## Install additional tools

```
brew install s3cmd jq
sudo easy_install pip
pip install ansible --user
```

> Note: It is better to install `ansible` with `pip` rather than with `brew`. This way `ansible` is available to Python when running certain scripts for getting dynamic inventory when provisioning.

## Test it!

Run the following commands in a terraform base directory to check if it works.

```
envchain aws terraform init
envchain aws terraform plan
```

## Pagerduty API token 
Some of the Terraform-modules require access to the Pagerduty REST API. To copy the access token into your `envchain` namespace, run this command:

`$ pass git pull && (pass show vy/pagerduty/apitoken | envchain -s aws PAGERDUTY_TOKEN)`

---
The tools has borrowed a lot from: https://github.com/digipost/cloud-tools


