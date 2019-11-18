Vagrant.configure("2") do |config|

# Con esto le indicamos a Vagrant ue vaya al directorio de "cajas" (boxes) que contiene su Atlas e instale un
  # Ubuntu 64 bits mediante el gestor de maquinas virtuales VirtualBox
  # El directorio completo de boxes se puede ver en la siguiente URL atlas.hashicorp.com/boxes/search
  config.vm.box = "ubuntu/bionic64"

  # Redirecciono puertos desde la maquina virtual a la maquina real. Por ejemplo 
  # del puerto 80 (web) de la maquina virtual con Debian se podrá acceder a través
  # del puerto 8081 de nuestro navegador.
  # Esto se realiza para poder darle visibilidad a los puertos de la maquina virtual 
  # y además para que no se solapen los puertos con los de nuestra equipo en el caso de que
  # ese número de puerto este en uso.
  config.vm.network "forwarded_port", guest: 80, host: 8081
  # configuración del nombre de maquina 
  config.vm.hostname = "utn-devops-equipo3.localhost"
  config.vm.provider "virtualbox" do |v|
	v.name = "marcelofransoy-vagrant-ubuntu"
  end  
  # Mapeo de directorios que se comparten entre la maquina virtual y nuestro equipo. En este caso es
  # el propio directorio donde está el archivo  y el directorio "/vagrant" dentro de la maquina virtual.
  config.vm.synced_folder ".", "/vagrant"
  # Copia el archivo de configuración del servidor web
  config.vm.provision "file", source: "Configs/devops.site.conf", destination: "/tmp/devops.site.conf"
  # En este archivo tendremos el provisionamiento de software necesario para nuestra 
  # maquina virtual. Por ejemplo, servidor web, servidor de base de datos, etc.
  config.vm.provision :shell, path: "Vagrant.bootstrap.sh", run: "always"
  
end
