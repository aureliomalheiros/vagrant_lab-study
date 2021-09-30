hosts = {
    "apt"   => {"memory" => "1024", "cpu" => "2", "ip" => "100", "image" => "ubuntu/bionic64"},
    "yum"   => {"memory" => "1024", "cpu" => "2", "ip" => "120", "image" => "centos/7"},
}

Vagrant.configure ("2") do |config|
    hosts.each do |name, conf|
        config.vm.define "#{name}" do |server|
            server.vm.box = "#{conf["image"]}"
            server.vm.hostname = "#{name}"
            server.vm.network "private_network", ip: "10.20.20.#{conf["ip"]}"
            server.vm.provider "virtualbox" do |metric|
                metric.name = "#{name}"
                metric.memory = conf["memory"]
                metric.cpus = conf["cpu"]
                metric.customize ["modifyvm", :id, "--groups", "/LPI"]
            end
        end
    end
end