# jarvisdo
🤖 Auto deploy services in clusters.

## Build
Install Python 3.x in control node:
```shell
cd /opt/soft
wget https://www.python.org/ftp/python/3.9.16/Python-3.9.16.tgz

mkdir -m 755 -p /usr/local/python/3.9.16
cd /opt/soft
tar zxvf Python-3.9.16.tgz
cd /opt/soft/Python-3.9.16
./configure --prefix=/usr/local/python/3.9.16 --enable-optimizations --enable-shared
make altinstall

cp /usr/local/python/3.9.16/lib/libpython3.so /usr/lib64/
cp /usr/local/python/3.9.16/lib/libpython3.9.so.1.0 /usr/lib64/
cd /usr/lib64
ln -s libpython3.9.so.1.0 libpython3.9.so

ln -s /usr/local/python/3.9.16/bin/python3.9 /usr/bin/python3
ln -s /usr/local/python/3.9.16/bin/pip3.9 /usr/bin/pip3
```
Install Ansible:
```shell
pip3 install ansible -i https://mirrors.aliyun.com/pypi/simple --trusted-host mirrors.aliyun.com
# make link
ln -s /usr/local/python/3.9.16/bin/ansible /usr/bin/ansible
ln -s /usr/local/python/3.9.16/bin/ansible-playbook /usr/bin/ansible-playbook
```
If we run ansible get error like:
```shell

TASK [Gathering Facts] ***********************************************************************************************************************************************************************************************************
fatal: [xxx.xxx.xxx.xxx]: FAILED! => {"msg": "to use the 'ssh' connection type with passwords or pkcs11_provider, you must install the sshpass program"}
```
Usually we run it directly:
```shell
yum install sshpass -y
```
When use RedHat-8.x and we are not register:
```shell
dnf --assumeyes install wget gcc gcc-c++ libgcc ;
wget http://sourceforge.net/projects/sshpass/files/latest/download -O sshpass.tar.gz  ;
tar -xvf  *.gz  ;
cd  ./sshpass*  ;
./configure    ;
make         ;
make install  ;
/usr/local/bin/sshpass -V  ; ## 1.06
```

## Usage
