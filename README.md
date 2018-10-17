# Terrafile [![Build Status](https://circleci.com/gh/coretech/terrafile.svg?style=shield)](https://circleci.com/gh/coretech/terrafile)

Terrafile is a binary written in Go to systematically manage external modules from Github for use in Terraform. See this [article](http://bensnape.com/2016/01/14/terraform-design-patterns-the-terrafile/) for more information on how it was introduced in a Ruby rake task.

This is currently an experimental WIP.

An example Terrafile:
```
tf-aws-vpc:
    source:  "git@github.com:terraform-aws-modules/terraform-aws-vpc"
    version: "v1.46.0"
tf-aws-vpc-experimental:
    source:  "git@github.com:terraform-aws-modules/terraform-aws-vpc"
    version: "master"
```

## How to install

### macOS

```sh
brew tap coretech/terrafile && brew install terrafile
```

### Linux
Download your preferred flavor from the [releases](https://github.com/coretech/terrafile/releases/latest) page and install manually.

For example:
```sh
curl -L https://github.com/coretech/terrafile/releases/download/v0.2/terrafile_0.2_linux_amd64.tar.gz | tar xz -C /usr/local/bin
```

## How to use

Terrafile config in current directory and modules exported to ./vendor/modules
```sh
$ terrafile
INFO[0000] [*] Checking out v1.46.0 of git@github.com:terraform-aws-modules/terraform-aws-vpc  
INFO[0000] [*] Checking out master of git@github.com:terraform-aws-modules/terraform-aws-vpc  
```

Terrafile config in custom location
```sh
$ terrafile -f config/
INFO[0000] [*] Checking out v1.46.0 of git@github.com:terraform-aws-modules/terraform-aws-vpc  
INFO[0000] [*] Checking out master of git@github.com:terraform-aws-modules/terraform-aws-vpc  
```

Terraform modules exported to custom location
```sh
$ terrafile -p custom_directory
INFO[0000] [*] Checking out master of git@github.com:terraform-aws-modules/terraform-aws-vpc  
INFO[0001] [*] Checking out v1.46.0 of git@github.com:terraform-aws-modules/terraform-aws-vpc  
```