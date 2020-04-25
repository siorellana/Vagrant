# Vagrant

En este repositorio encontrarán algunas definiciones de Vagrantfiles para distintos usos.

## Términos y definiciones

* BOX: Un ambiente preempaquetado de Vagrant que es el mismo en cualquier computador que es desplegado.

* PROVIDER: El sistema que administra la máquina virtual, como ViatualBox, VMWare, Hyper-V etc...

* PROVISIONER: Sistema que permite instalar software o configuraciones como CHEF o PUPPET.

* VAGRANTFILE: Un archivo único usado para definir el ambiente de Vagrant. Se escribe en Ruby.

## Comandos

`vagrant init`
>> Inicializa el ambiente y crea un Vagranfile

`vagrant box add <boxname>`
>> Add a Vagrant box to to environment.

`vagrant up`
>> Create and configure the guest machine(s) defined in the Vagrantfile.

`vagrant ssh`
>> SSH into a guest machine; include hostname in multi-machine environments.

`vagrant halt`
>> Attempt a graceful shutdown of the guest machine(s)

`vagrant suspend`
>> Suspend the machine(s) in its current state; does not shut down machine(s).

`vagrant resume`
>> Start stopped guest machine(s), whether halted or suspended.

`vagrant reload`
>> Reboot guest machine; the same as running vagrant halt then vagrant resume.

`vagrant status`
>> View state of machines managed by Vagrant

`vagrant destroy`
>> Remove guest machine(s).

`vagrant ssh`
>> Se accede a la VM a través de SSH.

## Ejemplos

```Ruby
# The $samplescript variable uses Ruby to feed in a script that runs upon
# provisioning:
$samplescript = <<SCRIPT
yum install -y httpd
systemctl enable httpd
systemctl start httpd
SCRIPT
# Define Vagrant configuration version (2):
Vagrant.configure(2) do |config|
# Define what box to use (CentOS 7):
 config.vm.box = "centos/7"
# Define hostname (myhost); most useful for environments with multiple guests:
 config.vm.hostname = "myhost"
# Configure private network IP address:
 config.vm.network "private_network", ip: "192.168.50.10"
# Sync files between local src/ folder and guest /var/www/html folder:
 config.vm.synced_folder "src/", "/var/www/html"
# Provision guest with $samplescript variable; uses shell scripting:
 config.vm.provision "shell", inline: $samplescript
# Set guest options for VirtualBox, including memory (1024), and CPU (2):
 config.vm.provider "virtualbox" do |vb|
 vb.memory = "1024"
 vb.cpus = "2"
 end
end
```
