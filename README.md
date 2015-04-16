# dnsmasq-automatic-update
A utility if using docker for dynamically updating DNS if using dnsmasq

# Pre-Requisites
* You need to install dnsmasq

# DNSMASQ configuration file
```
cat > /etc/dnsmasq.d/docker.conf << EOF
interface=docker0
conf-dir=/opt/docker/dnsmasq.d
EOF

sudo service dnsmasq restart
```

# Usage
A helpful development related utilty for dynamically updating DNS when a Docker container starts up.  The `detect-update` script runs in the background listening for running containers.  When it finds one, it will either add/update a dnsmasq entry.

NOTE: Since I didn't spend a lot of time on these scripts they all need to be in the same directory.  I have not actually tested if this will work with chkconfig, initctl or upstart.

## To start the detector in the background
```
sudo ./dnsmasq-update start
```

## To stop the detector
```
sudo ./dnsmasq-udpate stop
```

## To check the status of the detector
It's running if the status code is 0, otherwise it is not running.
```
sudo ./dnsmasq-update status
echo $?
```

NOTE: These scripts were written in 30 minutes, so if you find issues/bugs please submit a pull request and i'll get to it ASAP.  I'm also very open to feedback if you find this useful or not.

# Issues
Please submit pull requests if/when you find an issue and I'll be happy to review and merge.
