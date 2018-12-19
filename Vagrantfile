Vagrant.configure(2) do |config|

  config.vm.define "gitlab" do |conf|
    conf.vm.box = "centos/7"
    conf.vm.hostname = 'gitlab.example.com'
    conf.vm.network "private_network", ip: "172.24.0.11"
    conf.vm.provider "virtualbox" do |v|
      v.memory = 2048
      v.cpus = 2
    end
    conf.vm.provision "shell", inline: $inline_script
  end

  config.vm.define "jenkins" do |conf|
    conf.vm.box = "centos/7"
    conf.vm.hostname = 'jenkins.example.com'
    conf.vm.network "private_network", ip: "172.24.0.12"
    conf.vm.provider "virtualbox" do |v|
      v.memory = 2048
      v.cpus = 2
    end
    conf.vm.provision "shell", inline: $inline_script
  end
end

$inline_script = <<SCRIPT
# Inline Script starts
cat <<EOF > /etc/hosts
127.0.0.1   localhost localhost.localdomain
172.24.0.11 gitlab.example.com gitlab
172.24.0.12 jenkins.example.com jenkins
EOF

yum install -y git
git config --global user.name "Root User"
git config --global user.email admin@example.com
git config --global push.default simple
# Inline script ends
SCRIPT
