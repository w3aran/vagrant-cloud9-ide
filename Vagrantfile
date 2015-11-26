# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  config.vm.box = "ubuntu/trusty64"
  config.vm.network "private_network", ip: "10.0.0.222"
  config.vm.provision "shell", privileged: false, inline: $INSTALL_NODEJS
  config.vm.provision "shell", privileged: false, inline: $INSTALL_CLOUD9_IDE
  config.vm.provision "shell", privileged: false, run: "always", inline: $START_CLOUD9_IDE

end

$INSTALL_NODEJS = <<SCRIPT

mkdir /home/vagrant/SETUP_TEMP_DIR
cd /home/vagrant/SETUP_TEMP_DIR
echo "Install Ansible"
wget -O - https://raw.githubusercontent.com/w3aran/ansible-setup/master/install_ansible_on_ubuntu_14.sh | sh
echo "Install Node.js using Ansible Playbook"
wget -q -O /home/vagrant/SETUP_TEMP_DIR/ansible-role.nodejs.tar.gz https://github.com/w3aran/ansible-role.nodejs/archive/v0.0.3.tar.gz
tar -C /home/vagrant/SETUP_TEMP_DIR/ -xzf /home/vagrant/SETUP_TEMP_DIR/ansible-role.nodejs.tar.gz
cd /home/vagrant/SETUP_TEMP_DIR/ && mv ansible-role.nodejs-0.0.3 ansible-role.nodejs
cd /home/vagrant/SETUP_TEMP_DIR/ansible-role.nodejs/tests && ansible-playbook site.yml -i inventory --connection=local
echo "Install forever"
sudo -iu vagrant npm install -g forever
rm -rf /home/vagrant/SETUP_TEMP_DIR

SCRIPT

$INSTALL_CLOUD9_IDE = <<SCRIPT

echo "Cloning Cloud9 Core"
cd /home/vagrant
git clone https://github.com/c9/core.git Cloud9IDE
echo "Install Cloud9 IDE"
cd Cloud9IDE
scripts/install-sdk.sh

SCRIPT

$START_CLOUD9_IDE = <<SCRIPT

echo "Start Cloud9 IDE Standalone application"
cd /home/vagrant/Cloud9IDE
forever start server.js -p 8181 -l 0.0.0.0 -a : -w "/vagrant/workspace"

SCRIPT
