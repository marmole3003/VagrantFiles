# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "cloud-image/debian-13"
  config.vm.hostname = "WordPress"
  config.vm.network "private_network", ip: "192.168.33.12"
  config.vm.network "forwarded_port", guest: 80, host: 8080

  config.vm.provider "libvirt" do |vb|

   vb.memory = "2048"
   vb.cpus = "4"

end

  config.vm.provision "shell", inline: <<-SHELL

    chsh -s /bin/bash vagrant

    apt-get update
    apt-get install -y apache2 libapache2-mod-php mariadb-server php php-mysql
    apt-get install -y php-mbstring php-xml php-curl php-zip php-bcmath php-intl

    echo "Listen 80" > /etc/apache2/ports.conf
        
    echo "Listen 8080" >> /etc/apache2/ports.conf

    echo "<h1>VM server</h1>" > /var/www/html/index.html
    
    echo "<?php phpinfo(); ?>" | tee /var/www/html/info.php

    systemctl restart apache2

  SHELL

end
