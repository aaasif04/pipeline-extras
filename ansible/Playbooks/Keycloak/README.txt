Step1: You need to change the variable mysql_local_install: False to True in keycloak-centos7/vars/main.yml, if you
are planning to install the mysql locally, other than RDS.
##################################################################################################################################
Step2: You need to create ansible vault for the following variables, using the command
ansible-vault create vault

vault_mysql_host: rds-hostname/localhost
vault_mysql_user: demo
vault_mysql_pass: demopass
vault_mysql_db: keycloak
vault_mysql_root_user: rdsroot
vault_mysql_root_pass: root-pass
vault_keycloak_admin: paiadmin
vault_keycloak_pass: admin-pass
##################################################################################################################################
Step3: If you want to check or change the keycloak version or url. please change it in keycloak-centos7/defaults/main.yml
##################################################################################################################################
Step4: If you want to check or change the mysql-server version for local install, please change it in centos5.7/defaults/main.yml
##################################################################################################################################
Step4: run ansible playbook as follows

ansible-playbook --ask-vault-pass -e @your_vault_file main.yml