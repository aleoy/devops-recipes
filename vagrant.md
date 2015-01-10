#init a box
vagrant init ubuntu/precise64

#start box
vagrant up

#delete a box
vagrant destroy

#installing guest additions
vagrant plugin install vagrant-vbguest

#creating a box from existing virtual machine
vagrant package
vagrant box add <boxname> package.box