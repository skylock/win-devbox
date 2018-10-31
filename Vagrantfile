# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "win2016-standard-ssh"
  # Port forward WinRM and RDP
  config.vm.network :forwarded_port, guest: 3389, host: 3389, id: "rdp", auto_correct:true
  # config.vm.communicator = "winrm"
  # config.vm.guest = :windows
  # config.vm.network :forwarded_port, guest: 5985, host: 5985, id: "winrm", auto_correct:true
  # Port forward SSH
  # config.vm.network :forwarded_port, guest: 22, host: 2222, id: "ssh", auto_correct:true

  config.vm.provider :virtualbox do |v, override|
    v.gui = false
    v.customize ["modifyvm", :id, "--memory", 6144]
    v.customize ["modifyvm", :id, "--cpus", 1]
    v.customize ["modifyvm", :id, "--vram", "256"]
    v.customize ["modifyvm", :id, "--monitorcount", "2"]
    # v.customize ["setextradata", "global", "GUI/MaxGuestResolution", "any"]
    # v.customize ["setextradata", :id, "CustomVideoMode1", "1024x768x32"]
  end
  config.vm.provision :shell, :inline  => "Get-NetConnectionProfile | Set-NetConnectionProfile -NetworkCategory Private"
end