# one2influx

One2influx is small ruby daemon for getting monitoring data from [OpenNebula's XML-RPC API (4.12)](http://docs.opennebula.org/4.12/integration/system_interfaces/api.html) and storing it to [InfluxDB (0.9)](http://influxdb.com/). It needs Ruby 2+ to run.

### Installation
For Debian 8, install it as local gem:
```bash
$ sudo apt-get install ruby ruby-dev libghc-zlib-dev -y
$ gem install one2influx
```
or build it on your own:
```
$ sudo apt-get install ruby ruby-dev libghc-zlib-dev -y
$ git clone https://github.com/zidekmat/one2influx.git
$ cd one2influx && gem install bundle && bundle install
```
build on OL7:
```
# add software collections repo
[ol7_software_collections]
baseurl = https://yum$ociregion.oracle.com/repo/OracleLinux/OL7/SoftwareCollections/x86_64
enabled = 1
gpgcheck = 1
gpgkey = file:///etc/pki/rpm-gpg/RPM-GPG-KEY-oracle
name = Oracle Linux $releasever Software Collections ($basearch)
```
```
$ yum install ruby-devel ghc-zlib-devel rh-ruby23-rubygem-bundler rh-ruby23-ruby-devel git -y
$ git clone https://github.com/zidekmat/one2influx.git
$ cd one2influx && source /opt/rh/rh-ruby23/enable && bundle install
```

Then just set up your connection with ONE and InfluxDB and run
```bash
$ one2influx &
```

### Settings
Can be found in ***lib/one2influx/config.rb***. By default logs are stored in the directory from which the script was executed.

### Testing
You can run this without working ONE instance. Executable ***test/one2influx_fake*** will provide you with some testing XML data that can be modified in ***test/fake_lib/fake_one.rb***.
