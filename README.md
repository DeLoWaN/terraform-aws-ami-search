AWS AMI SEARCH Terraform module
=================================

Terraform module to find the last version of an AWS Ami IDs for working region, using common os name.

Why this repository and not the original one ?
--------

The [original repo](https://github.com/otassetti/terraform-aws-ami-search) has a PR with compatibility with Terraform >= 0.12 since September 2020 and not accepted. The original author seems not active on Github since 2019.

Terraform versions
--------
Terraform 0.12 and later. Pin module version to ~> v1.0. Submit pull-requests to master branch.

Terraform 0.11. Pin module version to ~> v0.1. Submit pull-requests to terraform011 branch.

Usage
--------

Set the 'os' var from the below list:

``` bash
# Linux
ubuntu -> ubuntu-16.04
ubuntu-14.04
ubuntu-16.04
centos -> centos-7
centos-6
centos-7
centos-8
rhel -> rhel-7
rhel-6
rhel-7
rhel-8
debian -> debian-9
debian-8
debian-9
debian-10
fedora-27
amazon
amazon-2_lts
suse-les -> suse-les-12
suse-les-12


# Windows
windows -> windows-2019-base
windows-2019-base
windows-2016-base
windows-2012-r2-base
windows-2012-base
windows-2008-r2-base
```

Examples
--------

```hcl
module "ami-search" {
  source  = "otassetti/ami-search/aws"
  os = "centos-7"
}

resource "aws_instance" "web" {
  ami = module.ami-search.ami_id
  instance_type = "t2.micro"

  tags {
    Name = "HelloWorld"
  }
}


```

Limitations
-----------

* Hvm type only (Hardcoded in the filter module)

Authors
-------

Module managed by [Olivier Tassetti].

License
-------

Apache 2 Licensed. See LICENSE for full details.
