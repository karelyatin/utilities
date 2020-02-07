# Steps to setup centos8 mock on centos7 system

# Update system
# Faced ImportError: No module named _conf with CentOS7.5 and dnf from epel

sudo yum update -y
sudo yum -y install git createrepo mock \
gcc redhat-rpm-config rpmdevtools httpd libffi-devel openssl-devel \
yum-utils dnf
sudo usermod -a -G mock $USER
sudo chmod -R o+x /home/$USER
newgrp mock;newgrp $USER

sudo yum install -y epel-release
sudo yum -y update mock
sudo yum -y remove epel-release

# Create /etc/mock/centos-8-x86_64.cfg from ./centos-8-x86_64.cfg

To test:-
mock -r centos-8-x86-64 --shell
