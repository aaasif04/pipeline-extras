##########################################################################################
#For OpenVPN server installation
#Set OpenVPN server specific variables in openvpn-centos7/vars/main.yml

#Specify subnet for the vpn network
openvpn_network: 172.30.0.0

#Specify OpenVPN certificate creation variables here:
KEY_COUNTRY: IN
KEY_PROVINCE: Kerala
KEY_CITY: Cochin
KEY_ORG: "Prevalent AI"
KEY_EMAIL: "support@prevalent.ai"
KEY_CN: cear-qa.prevalent.ai
##########################################################################################

#For openvpn client add
#Set OpenVPN Client specific variables in openvpn-centos7/vars/main.yml

#Specify the username need to create the client certificates. Use comma seperated ones, if more than one username

vpn_username: test
or
vpn_username: test,test1,test2,test3
##########################################################################################

#Created paasword and ovpn file will be downloaded to Credentials fiolder inside PLAYBOOK Directory 