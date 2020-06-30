# Fingerprint_Database_Generator
The MITMEngine project (https://github.com/cloudflare/mitmengine) detects HTTPS interception and user agent spoofing by checking if the TLS fingerprint of an incoming connection corresponds to the expected fingerprint for the connection’s user agent. MITMEngine powers the MALCOLM dashboard (https://malcolm.cloudflare.com). The goal of this project is to use BrowserStack to generate TLS client hello fingerprints and user agents for a selection of recent browsers and store them in a Postgres database.


## Steps
1- Install version 12.3 postgresql on Mac using: https://www.robinwieruch.de/postgres-sql-macos-setup

2- Create postgresql database with a table listing the http fingerprints, a table listing the tls fingerprints and a third table storing the matching of their respective ids. 

3- Create an account on BrowserStack (a free account would be enough for this project); automate browserstack for python using https://www.browserstack.com/automate/python. 
