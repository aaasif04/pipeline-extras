Step 1. Modify varaibles in groups_vars/all/var

Step 2. Create a vault file using the following variables, that is using in var file

ansible-vault create group_vars/all/vault

#Sample contents goes here
vault_tsm_sudo_user: paitableau
vault_tsm_sudo_user_pass: paitableau@Pass20
vault_tsm_zip: 682305
vault_tsm_country: India
vault_tsm_city: Cochin
vault_tsm_last_name: Doe
vault_tsm_industry: IT
vault_tsm_title: Engineer
vault_tsm_phone: 9874563217
vault_tsm_company_name: DataCompany
vault_tsm_state: Kerala
vault_tsm_department: IT
vault_tsm_first_name: john
vault_tsm_email: lnamefname24@yopmail.com
vault_tsm_tableau_admin_user: tableauadmin
vault_tsm_tableau_admin_password: TableadminPass1

