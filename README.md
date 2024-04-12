# Atlantis integration with GitHub

## Commands to install Docker in Amazon Linux 3

```
sudo yum update -y
sudo yum search docker -y
sudo yum install docker -y
sudo systemctl enable docker.service
sudo systemctl start docker.service
sudo systemctl status docker.service
```

## To Build the Docker Image

``` docker build -t atlantis . ```

## To Run Atlantis as Docker contianer

``` docker run -itd -p 4000:4141 --name atlantis atlantis server --automerge --autoplan-modules --gh-user=<github-account-username> --gh-token=<github-usr-access-token> --repo-allowlist=<list of allowed repos> ```

### Example for above command with single repository

```docker run -itd -p 4000:4141 --name atlantis atlantis server --automerge --autoplan-modules --gh-user=jerinrathnam --gh-token=ghp_lj8nNeckni0N#C*54urnDBUCc0h3f#BFU --repo-allowlist=github.com/easydeploy-cloud/terraform-atlantis```

### Example for above command with all repositories in a GitHub account or organization

``` docker run -itd -p 4000:4141 --name atlantis atlantis server --automerge --autoplan-modules --gh-user=jerinrathnam --gh-token=nNeckni0N#C*54urnDBUCc0h3f#BFU --repo-allowlist=github.com/easydeploy-cloud/* ```

## To ssh into the Atlantis Docker Container

``` docker exec -it atlantis /bin/sh ```

## To edit the aws credentials file

```vi /home/atlantis/.aws/credentials ```

### Add the following content into the credentials file

```
[default]
aws_access_key_id = <ACCESS-KEY>
aws_secret_access_key = <SECRET-KEY>
```

### Replace the following values in the above code

**ACCESS-KEY:** Access key ID of the AWS IAM user

**SECRET-KEY:** Secret Access key ID of the AWS IAM user

**Note:** If you have many profiles you can make entries accordingly in the above file and use it in the Terraform

## To push the code to GitHub
```
git add *
git commit -m "Create EC2 Instance"
git checkout -b develop
git push origin develop
```

## Atlantis commands to reference
``` atlantis plan -d . ``` ⇨ to get a plan of the terraform code

``` atlantis apply -d . ``` ⇨ to apply the terraform code

For more reference for Atlantis commands: [Atlantis Commands](https://www.runatlantis.io/docs/using-atlantis.html)

To find more blogs about Terraform: [Terraform Blogs](https://www.easydeploy.io/blog/category/terraform/)
