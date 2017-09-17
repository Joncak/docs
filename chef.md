Instalar ChefDK
===============
curl https://omnitruck.chef.io/install.sh | sudo bash -s -- -P chefdk -c stable -v 0.18.30

cookbooks
=========
chef generate cookbook dont_starve
chef generate template index.html

knife
======

knife ssl check
knife node delete node1-centos --yes
knife cookbook delete learn_chef_httpd --all --yes
knife cookbook upload cookbook-name
knife cookbook list
knife node delete server -y && knife client delete server -y
knife bootstrap ADDRESS --ssh-user USER --sudo --identity-file IDENTITY_FILE --node-name node1-centos --run-list 'recipe[learn_chef_httpd]'
knife bootstrap localhost --ssh-port PORT --ssh-user vagrant --sudo --identity-file IDENTITY_FILE --node-name node1-centos --run-list 'recipe[learn_chef_httpd]'
knife ssh 'name:node1-centos' 'sudo chef-client' --ssh-user vagrant --identity-file ~/.ssh/private_key --attribute ipaddress

This work for the kitchen && vagrant && node setup
--------------------------------------------------
knife ssh localhost --ssh-port 2222 'sudo chef-client' --ssh-user vagrant --identity-file ~/learn-chef/.vagrant/machines/default/virtualbox/private_key --manual-list

Roles
-----
knife role from file roles/web.json
knife node run_list set nisum-node 'role[web]'
knife status 'role:web' --run-list
knife role delete web --yes


Test Kitchen
============
kitchen exec -c 'curl localhost'

