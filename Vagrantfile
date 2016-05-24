# -*- mode: ruby -*-
# vi: set ft=ruby :

$script = <<SCRIPT
  mkdir -p bin SpiderOakONE
  cd SpiderOakONE

  wget "https://spideroak.com/getbuild?platform=fedora&arch=x86_64" --output-document spideroak.rpm --quiet
  rpm2cpio spideroak.rpm | cpio -vid
  rm spideroak.rpm

  cd ..
  cp SpiderOakONE/usr/bin/SpiderOakONE bin/
  sed -i bin/SpiderOakONE -e "s/\\/opt/\\$HOME\\/SpiderOakONE\\/opt/"

  chown -R vagrant:vagrant bin SpiderOakONE

  echo "run ./bin/SpiderOakONE"
SCRIPT

Vagrant.configure(2) do |config|
  config.vm.box = "bento/centos-6.7"
  config.vm.provision "shell", inline: $script
end
