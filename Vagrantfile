# -*- mode: ruby -*-
# vi: set ft=ruby :
@ansible_home = "/vagrant"

Vagrant.configure("2") do |config|
  config.vm.define "certbot-route53"
  config.vm.box = "generic/ubuntu2004"

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "test.yml"
    ansible.config_file = "ansible.cfg"
    ansible.galaxy_role_file = "requirements.yml"
    ansible.become = true
    ansible.extra_vars = "test-vars.yml"
    ansible.vault_password_file = "vault-passwd"
  end
end
