# aws_promgraf_tf
This set of terraform files are useful if you want a quick setup of prometheus, node exporter
and grafana server, for demo or education or testing purpose. The images uses Ubuntu and 
the shell scripts are written (with help from Grok) for Ubuntu. If you want to use different
images, you should also ensure that the shell scripts will work with them.

# TO DO BEFORE RUNNING TERRAFORM
- Update variable-tf to your local values
- Name of the key pair in AWS is terraform-key, this should match variables.tf
- Create a /private-key folder and copy the PEM key-pair file download from aws
  - Rename the key-pair file to terraform-key.pem, this should match nullresources_provisions.tf
  - On Windows, you need to remove "Authenicated Users" and "Users" from folder permissions
  - If you are not admin, you must add yourself with full control before removing those groups.

# Things to note
- nullresource is used to setup scraping of the node exporter in prometheus
  - a delay is required since it takes awhile to get the IP of the node exporter
  - and we need to wait for prometheus to setup before we can update the prometheus.yml file
- Grafana uses the default admin for logon (port 3000)
- Security groups are setup such that all public IP are only accessible from your desktop's IP address.
  this is to ensure that you servers are not exposed to everyone.
- You need to manually add prometheus as data source in Grafana.

# IMPORTANT
- Always destroy all resource once you are done testing the servers.

# LAST TESTED WORKING
- 2026-03-17