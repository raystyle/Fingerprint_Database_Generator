# Fingerprint_Database_Generator
The MITMEngine project (https://github.com/cloudflare/mitmengine) detects HTTPS interception and user agent spoofing by checking if the TLS fingerprint of an incoming connection corresponds to the expected fingerprint for the connection’s user agent. MITMEngine powers the MALCOLM dashboard (https://malcolm.cloudflare.com). The goal of this project is to use BrowserStack to generate TLS client hello fingerprints and user agents for a selection of recent browsers and store them in a Postgres database.


## Steps

MacOS

1- Install version 12.3 postgresql on Mac using: https://www.robinwieruch.de/postgres-sql-macos-setup;  you can run "brew install postgresql"

2- Create postgresql database with a table listing the http fingerprints, a table listing the tls fingerprints and a third table storing the matching of their respective ids (run script ). 

3- Create an account on BrowserStack (a free account would be enough for this project); automate browserstack for python using https://www.browserstack.com/automate/python. 
  * install behave-browserstack (https://github.com/browserstack/behave-browserstack.git) -- not sure this is compulsory
  
4- Download and install mitmengine 
  * setup Go ( https://golang.org/dl/go1.14.4.linux-amd64.tar.gz) using https://golang.org/doc/install
  * install and run vendering or gomo logic using https://gocodecloud.com/blog/2016/03/29/go-vendoring-beginner-tutorial/ --not sure
  * Use Go 1.14.1 (go version go1.14.4 linux/amd64 for linux and go1.14.4 darwin/amd64 for macOS). In case you needed to uninstall Go, use https://stackoverflow.com/questions/42186003/how-to-uninstall-golang
  * set GOPATH to /home/username/go/
  * run ``make test`` and ``make cover`` in ```/home/username/go/src/github.com/cloudflare/mitmengine```
  
  
Ubuntu
 
 1- Install version 12.3 postgresql on Ubuntu using: https://www.postgresql.org/docs/9.0/tutorial-install.html
  * In case you get the error 'createdb: could not connect to database template1: FATAL:  Peer authentication failed for user "postgres"',  run `sudo nano /etc/postgresql/10/main/pg_hba.conf` and replace `local   all             postgres                                peer` by `local   all             postgres                                trust`; 


## Writeup on design choices
