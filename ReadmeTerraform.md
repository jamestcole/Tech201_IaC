# Terraform Documentation

Set up terraform from the following address.
https://developer.hashicorp.com/terraform/downloads

## Change variable for private and public keys

Go to control panel, settings , system properties and environment variables. The access key and secret key can be put in the user variable whearas the path can be put in the System variales . click new to creake new user variables and edit to edit your path in system variables

It should look something like this.

```
AWS_ACCESS_KEY_ID       pasteaccesskeyhere
AWS_SECRET_ACCESS_KEY   pastesecretkeyhere
```

In system variables, path
```
C:\terraform
```

Make a new directory next to your ansible directory for convenience, in my case Tech201_IaC/terraform.

then you can check that terrform is active there.
```
terraform --version
```
The main.tf file needs to be written and put in this folder. The follwoing can used as a template. Remember to replace the appropiate text with the correct settings from your AMI.

```
provider "aws" {
    region = "eu-west-1"

}
resource "aws_instance" "app_instance" {
  ami = "ami-09a9582ce47915c82"
  instance_type = "t2.micro"
  associate_public_ip_address = true
  tags = {
    Name = "tech201-James-terraform-app"
  }
}
```

After it has been written and saved and gitbash reopened in admin mode. The following commands can be used to initialise,  plan and then apply the deployement of ec2 instances.

```
terraform init
terraform plan
terraform apply
```
When we are done, we can used the following to terminate.
```
terraform destroy
```

Remember to add your terraform files to your `.gitignore` if it was made in your IDE.