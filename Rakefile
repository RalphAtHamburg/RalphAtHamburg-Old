#
# Rakefile from https://gist.github.com/1902178#file_rakefile
# http://scottwb.com/blog/2012/02/24/middleman-deployment-rakefile/
#

SSH_USER = 'user'
SSH_HOST = 'www.example.com'
SSH_DIR  = '/var/www/html/www.example.com'

desc "Build the website from source"
task :build do
  puts "## Building website"
  status = system("middleman build --clean")
  puts status ? "OK" : "FAILED"
end

desc "Run the preview server at http://localhost:4567"
task :preview do
  system("middleman server")
end

desc "Deploy website via rsync"
task :deploy do
  puts "## Deploying website via rsync to #{SSH_HOST}"
  status = system("rsync -avze 'ssh' --delete build/ #{SSH_USER}@#{SSH_HOST}:#{SSH_DIR}")
  puts status ? "OK" : "FAILED"
end

desc "Build and deploy website"
task :gen_deploy => [:build, :deploy] do
end