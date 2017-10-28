# Linux Server Configuration Project

# Connection information

IP: 52.91.57.63
SSH port: 2200

# URL

[http://52.91.57.63/](http://52.91.57.63/)

# Task Summary

* Configured the firewall and ssh
  * Allow ssh from port 2200 through ufw and Lightsale
  * Opened ports 80 (http) and 123 (ntp) in ufw
  * Changed the ssh config to use port 2200
  * Enabled ufw
  * Removed access to ssh on port 22
* Gave `grader` access
  * `sudo adduser grader` and filled out some information
  * `sudo usermod -aG sudo grader` to add grader into the sudo group
  * Created an SSH key pair locally with PuTTY
  * `su - grader` to use the grader account
    * `mkdir ~/.ssh`
    * `nano ~/.ssh/authorized_keys` and copy and pasted the grader public key
    * Setup PuTTY to use the grader account/key to test ssh and sudo
* `cat /etc/timezone` to find the timezone was set to Etc/UTC
* `sudo apt-get ...` (I think this step would have been a little easier if I had used a python venv)
  * `apache2`
  * `libapache2-mod-wsgi`
  * `python-flask`
  * `python-sqlalchemy`
  * `python-oauth2client`
  * `python-httplib2`
  * `python-requests`
  * `postgresql`
  * `python-psycopg2`
* I neeeded to make changes to file references in my Item Catalog application (needed full paths instead of relative ones)
* I needed to reconfigure the Item Catalog production settings
  * Mostely PosgreSQL stuff (http://docs.sqlalchemy.org/en/latest/core/engines.html)
* Used http://flask.pocoo.org/docs/0.12/deploying/mod_wsgi/ to help get the `.wsgi` script setup
* Constantly referred to the PosgreSQL docs to get it setup (https://www.postgresql.org/docs/9.5/static/)
* Some errors did not show up in the apache error log so I used http://flask.pocoo.org/docs/0.12/errorhandling/ to setup a log file.
  * I also had to `chmod 666 error.log` so that I could log flask errors (probably not perfect, but got it working)
