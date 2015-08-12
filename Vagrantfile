Vagrant.configure(2) do |config|
  config.vm.synced_folder "./www", "/var/www"   # Sync'd folder

  config.vm.provider "docker" do |d|
    d.build_dir = "./Docker" # specifies the path to the Dockerfile
    d.ports = ['8080:80']     # Forwards port 8080 from the host to the Docker Container port 80
  end
end
