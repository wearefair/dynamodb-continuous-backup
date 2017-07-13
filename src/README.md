## Fair Setup Steps

### Prereqs
- All of the IAM roles as outlined in the root of this project. It's highly recommended you use the Terraform repo with the services/dynamodb-backups module to create them.

### Setting Up the Buckets
1. Create configuration file that details the IAM roles and buckets to be used. A good template to copy is stage_config.hjson. Following the naming convention of uniquename_config.hjson.
2. Create a provisioning file for continuous backup. A good template to copy is stage_provisioning_whitelist.hjson. Following the naming convention of uniquename_provisioning_whitelist.hjson.
3. Run `make release` to deploy configuration files with the PREFIX variable being the unique name you chose. Ex: `PREFIX=stage make release`. This will generate the configs and deploy them. This will deploy the stage_config.hjson file.
4. Run `make continuous` to deploy the provisioning whitelist config you wrote with the PREFIX variable being the unique name you chose for your file. Ex: `PREFIX=stage make continuous`. This will deploy the stage_provisioning_whitelist.hjson file.

### Restoring
Restoring from a backup takes some doing. 
