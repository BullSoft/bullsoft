Port from openshift
========
Only for ubuntu server, but not like that - 'cause we use ```sudo apt-get install``` in ```build``` script for instance.

Firstly, add these to your ~/.bashrc

```bash
export OPENSHIFT_DIY_DIR=$HOME
export OPENSHIFT_DIY_LOG_DIR=$HOME/log
export OPENSHIFT_DIY_IP=0.0.0.0
export OPENSHIFT_DIY_PORT=8080
export OPENSHIFT_REDIS_PORT=6379


export OPENSHIFT_REPO_DIR=$HOME
export OPENSHIFT_DATA_DIR=$HOME/.openshift/data
export OPENSHIFT_TMP_DIR=$HOME/.openshift/tmp

if [ -f ${OPENSHIFT_DATA_DIR}/.bash_profile ]; then
    . ${OPENSHIFT_DATA_DIR}/.bash_profile
fi
```

To make these effective, you should ```soure ~/.bashrc```.

Then, type these on terminal:

```bash
cd ~
git clone https://github.com/BullSoft/openshift.git
cd ~/openshift/action_hooks/
./build

```

      Maybe you have to type ```password``` to let it continue.


Finally, type:

```bash
cp -r ~/bullsoft/wwwroot ~/
```
... and the file structure would be like this


```
.
├── log
│   ├── access.log
│   ├── error.log
│   ├── php-fpm.log
│   └── redis_6379.log
├── openshift
│   ├── action_hooks
│   ├── README.md
│   ├── tmpl
│   └── wwwroot
├── run
│   ├── mysql.pid
│   ├── mysql.sock
│   ├── nginx.pid
│   ├── php-fpm.pid
│   ├── php-fpm.socket
│   └── redis_6379.pid
├── runtime
│   ├── etc
│   ├── haproxy
│   ├── libs
│   ├── mysql
│   ├── nginx
│   ├── php5
│   └── redis
└── wwwroot
    └── index.php
    
```    
