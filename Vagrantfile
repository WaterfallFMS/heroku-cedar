Vagrant::Config.run do |config|
  config.vm.box = "heroku"
  config.vm.box_url = "http://dl.dropbox.com/u/1906634/heroku.box"
  
  # guest port, local port
  config.vm.forward_port 3000, 3000
end

