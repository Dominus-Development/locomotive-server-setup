locomotive-server-setup
=======================

Generic Locomotive Server setup

Bash Instructions
-----------------
Install Dependencies:
```bash

apt-get update
apt-get install git build-essential zlib1g-dev libreadline-dev libssl-dev libcurl4-openssl-dev libxslt-dev libxml2-dev
```
Install Rbenv and Ruby-build:
```bash
git clone git://github.com/sstephenson/rbenv.git ~/.rbenv
git clone https://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(rbenv init -)"' >> ~/.bashrc
source ~/.bashrc

rbenv install 1.9.3-p448 && rbenv global 1.9.3-p448
rbenv rehash
```
Install Mongoid:
```bash
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10
echo 'deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen' | sudo tee /etc/apt/sources.list.d/10gen.list
sudo apt-get update

sudo apt-get install mongodb-10gen
echo "mongodb-10gen hold" | sudo dpkg --set-selections
```
Setup Mongo Admin User:
```bash
mongo
```
```mongodb
db.addUser("admin_username", "admin_password");    // Adding admin user

db.auth("admin_username ", "admin_password ");    // Authenticate admin user

db = db.getSiblingDB("newDatabase");   // use  database code from java script

db.addUser("database_username", "database_password");    // Adding newDatabase database user
```
Install ImageMagick:
```bash
apt-get install imagemagick
```
Clone Site Repo:
```bash
git clone https://github.com/Dominus-Development/site.git

cd site
gem install bundler
rbenv rehash
bundle install
cp config/environment_variables.yml.sample config/environment_variables.yml
nano environment_variables.yml
```

Edit Environment Variables File

Run Website:
```bash
bundle exec unicorn_rails
```
