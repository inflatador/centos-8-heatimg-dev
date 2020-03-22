Vagrant.configure("2") do |config|

  config.ssh.private_key_path = '~/.ssh/id_rsa'

  config.vm.synced_folder ".", "/vagrant",
  type: "rsync",
  rsync__exclude: ['.git/', 'cloud-init/'],
  rsync__verbose: true
  config.vm.provider :rackspace do |rs|
    rs.username         = ENV['NOVA_USERNAME']
    rs.server_name     = "centos8-heat-#{rand(00..99)}"
    rs.api_key          = ENV['NOVA_API_KEY']
    rs.rackspace_region = ENV['NOVA_REGION_NAME']
    rs.flavor           = "general1-1"
    rs.image            = "CentOS 8 (PVHVM)"
    rs.metadata         = {"created_by" => "vagrant"}       # optional
    rs.key_name = "ctrl"
    rs.config_drive 	= "true"
    rs.user_data = "./cloud-init/build-dev-env.yml"
  end
end
