SOURCES = [
  'deb http://archive.neon.kde.org/release xenial main',
  'deb-src http://archive.neon.kde.org/release xenial main'
].freeze

task :'repo::setup' do
  File.open('/etc/apt/sources.list.d/neon.list', 'w') do |f|
    SOURCES.each { |line| f.puts(line) }
  end
  sh 'apt-key adv --keyserver keyserver.ubuntu.com --recv 55751E5D'
  sh 'apt update'
end

task :generate do
  puts File.read('appname')
  ruby 'generate.rb'
end
task :generate => :'repo::setup'

task :snapcraft do
  sh 'apt install -y snapcraft'
  sh 'snapcraft'
end
task :snapcraft => :'repo::setup'
