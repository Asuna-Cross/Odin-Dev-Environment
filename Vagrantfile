$softwareinstall = <<-SCRIPT
echo 'deb http://download.opensuse.org/repositories/home:/ungoogled_chromium/Ubuntu_Focal/ /' | sudo tee /etc/apt/sources.list.d/home-ungoogled_chromium.list > /dev/null
curl -s 'https://download.opensuse.org/repositories/home:/ungoogled_chromium/Ubuntu_Focal/Release.key' | gpg --dearmor | sudo tee /etc/apt/trusted.gpg.d/home-ungoogled_chromium.gpg > /dev/null
sudo apt update
sudo apt install -y ungoogled-chromium
SCRIPT

Vagrant.configure("2") do |config|
    config.vm.box = "myaylaci/xubuntu2004-desktop"
    config.vm.provider "virtualbox" do |v|
        #turning on vb gui
        v.gui = true
        #Alotting memory
        v.memory = 2048
        # Bidirectional clipboard
        v.customize ["modifyvm", :id, "--clipboard", "bidirectional"]
    end
    config.vm.provision "shell", inline: $softwareinstall
end