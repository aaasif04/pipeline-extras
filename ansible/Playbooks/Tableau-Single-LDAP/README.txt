Step 1. Set the following varaibles in groups_vars/all/var


#Section 2 in vars file
Whether we need to activate the trial or not. If already have product key then set this to false
activate_trial = true 

Step 2: 
#Section 6 in vars file
Set the total number of additionnal nodes in the total_additional_nodes in #Section 6 . Please note, this is not including initial node

total_additional_nodes: 2

step 3 :
#Section 4 in vars file
Set the identity store here. values: Local (local identity store), AD (Active Directory), LDAP (Simple OpenLDAP) , LDAP-GSSAPI (LDAP with GSSAPI).
identity_store: LDAP

Step 4: Select the processes for each node , if cluster installation is doing.
#in Section 7


Step 5. Create a vault file using the following variables, that is using in var file

ansible-vault create group_vars/all/vault

#Sample contents goes here
#Section 2 in vars file
vault_product_key: xxxxxxxxxxx.xxxxxxxxxxx.xxxxxxxxxx #If you have product key, then creat this variable. Otherwise no need for the variable

#Section 1 in vars file
vault_tsm_sudo_user: sudouser # Unix sudo user in the server
vault_tsm_sudo_user_pass: password # password for the above user

#Section 3 in vars file
vault_tsm_zip: 682350 #Pin code
vault_tsm_country: India # Country
vault_tsm_city: Cochin #Local City
vault_tsm_last_name: Doe #Lat Name
vault_tsm_industry: IT # Company Industry
vault_tsm_title: Engineer #Job Title
vault_tsm_phone: 9874563217 #Company Phone number
vault_tsm_company_name: DataCompany #Company Name
vault_tsm_state: Kerala #State
vault_tsm_department: IT #Department
vault_tsm_first_name: john #First Name
vault_tsm_email: lnamefname24@yopmail.com #Mail id for registration

#Section 5 in vars file
vault_tsm_tableau_admin_user: tableauadmin #If you are using LDAP/AD, then this user must exists in LDAP/AD. If local identity store, this can be any name
vault_tsm_tableau_admin_password: TableadminPass1 #If you are using LDAP/AD, then this password for the above user must exists in LDAP/AD. If local identity store, this can be any password for the abve user

#Section 4 in vars file
vault_ldap_domain_name: domainname.local #LDAP DOMAIN NAME
vault_ldap_root_dc: dc=doaminname,dc=local #Root DC for LDAP
vault_ldap_server_hostname: ldap.server.hostanme #Ldap server hostname or IP
vault_ldap_port: 389 #LDAP Port
vault_ldap_admin_username: cn=ldapadm,dc=dc=doaminname,dc=local,dc=local #Admin LDAP User
vault_ldap_admin_password: Simple2200 #LDAP Admin password
vault_ldap_user_base_dn: ou=People,dc=dc=doaminname,dc=local,dc=local #User OU
vault_ldap_group_base_dn: ou=Group,dc=dc=doaminname,dc=local,dc=local #Group OU