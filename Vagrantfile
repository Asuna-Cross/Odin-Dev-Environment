require './gitinfo.rb'

$softwareinstall = <<-SCRIPT
sudo apt install git-all
curl -s -L https://go.microsoft.com/fwlink/?LinkID=760868 -o vscode.deb
dpkg -i vscode.deb
rm vscode.deb
SCRIPT

$vscodesetup = <<-SCRIPT
code --install-extension enkia.tokyo-night
SCRIPT

Vagrant.configure("2") do |config|
    config.vm.box = "generic/ubuntu2204"
    config.vm.provider "virtualbox" do |v|
        #turning on vb gui
        v.gui = true
        #Alotting memory
        v.memory = 2048
        # Bidirectional clipboard
        v.customize ["modifyvm", :id, "--clipboard", "bidirectional"]
    end
    config.vm.provision "shell", inline: $softwareinstall
    config.vm.provision "shell", inline: $vscodesetup, privileged: false
    config.vm.provision "shell", inline: $gitsetup, privileged: false
end