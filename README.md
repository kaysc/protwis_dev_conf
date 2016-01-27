Development configuration for Protwis on linux servers using Puppet

### Instructions

Tested on **Ubuntu 14.04** and **CentOS 7** (may need tweaks for other systems).

WARNING: Running this script changes the configuration of your system and may override important settings.

#### Install Git and Puppet

Debian based systems (Debian, Ubuntu)

    sudo apt-get -y install git puppet

RedHat based systems (RedHat, CentOS, Fedora)

    sudo yum -y install epel-release git
    sudo yum -y install puppet

#### Create and change to /protwis directory

    sudo mkdir /protwis
    sudo chown $USER /protwis
    cd /protwis

#### Clone the protwis repository

    git clone https://github.com/protwis/protwis sites/protwis

#### Clone this repository and name it "conf" (the name is important)

    git clone --recursive https://github.com/protwis/protwis_dev_conf.git conf

#### Change to the cloned repo directory

    cd conf

#### Run with Puppet

    sudo puppet apply --modulepath protwis_puppet_modules manifests/default.pp

#### Reload your shell

Close you current shell and open a new one to reload environment variables.

#### Start the Django development webserver

This example runs the server on port 8000, but you can also use another port. If you want to access the server on a
different machine, make sure the port you are using is open.

    cd /protwis/sites/protwis
    /env/bin/python3 manage.py runserver 0.0.0.0:8000

You're all set up. The webserver will now be accessible from http://localhost:8000
