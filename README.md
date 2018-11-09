### perftools-rb
---
https://github.com/tmm1/perftools.rb

```sh
curl -o 10_requests_to_homepage.gif "http://localhsot:3000/homepage?profile=true&times=10"

CPUROFILE=/tmp/my_app/profile \
RUBYOPT="-r`gem which perftools | tail -1`" \
ruby my_app.rb

pprof.rb --text /tmp/add_numbers/profile
pprof.rb --pdf /tmp/add_numbers_profile > tmp/add_numbers_profile.pdf
pprof.rb --gif /tmp/add_numbers_profile > /tmp/add_numbers_profile.gif
pprof.rb --callgrind /tmp/add_numbers_profile > /tmp/add_numbers_profile.grind
kcachegrind /tmp/add_numbers_profile.grind
pprof.rb --gif --focus=Integer /tmp/add_numbers_profile > /tmp/add_numbers_custom.gif
pprof.rb --text --ignore=Gem /tmp/my_app_profile

sudo gem install perftools.rb
git clone git://github.com/tmm1/perftools.rb
cd perftools.rb
gem build perftools.rb gemspec
gem install perftools.rb
gem 'perftools.rb', :git => 'git://github.com/tmm1/perftools.rb.git'
brew install graphviz ghostscript
sudo apt-get install graphviz ps2pdf

wget http://gperftools.googlecode.com/files/gperftools-2.0.tar.gz
tar zxvf gperftools-2.0.tar.gz
cd gperftools-2.0

// ./configure --prefix=/opt
make
sudo make install

export LD_PRELOAD=/opt/lib/libprofiler.so
export DYLD_INSERT_LIBARIES=/opt/lib/libprofiler.dylib
CPUROFILE=/tmp/ruby_interpreter.profile ruby -e ' 5_000_000.times{ "hello world" }'
pprof `which ruby` --text /tmp/ruby_interpreter.profile
```

```ruby
require 'rack/perftools_profiler'
config.middleware.us ::Rack::PerftoolsProfiler, :default_printer => 'gif'

require 'perftools'
PerfTools::CpuProfiler.start("/tmp/add_numbers_profile") do
  5_000_000.times{ 1+2+3+4+5 }
end

require 'perftools'
PerfTools::CpuProfiler.start("/tmp/add_numbers_profile")
5_000_000.times{ 1+2+3+4+5 }
PerfTools::CpuProfiler.stop

```

```
```
