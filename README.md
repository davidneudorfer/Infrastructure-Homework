Infrastructure-Homework
=======================

Requirements:

- VirtualBox 4.2.16
- Vagrant 1.2.3

run :<br>
`export PYTHONUNBUFFERED=1`<br>
and<br>
`export ANSIBLE_HOST_KEY_CHECKING=False`

before running:

`vagrant up`


========================
Provision a simple reverse-proxied LAMP infrastructure using the server orchestration software of your choice (puppet, chef, ansible, bash scripts). This infrastructure consists of two server systems, each running Centos 6 and the latest versions of available packages and services:

1) front with nginx, memcached
2) app with apache2, php5.3, mysql-server

The provisioning process should perform the following:

(1) Download and install the following PHP script into the document root of

test.php (included)

There may be other packages required on the servers to successfully execute the test.php script.
(2) Download and run the following sql script on app. After correctly loading, it should have loaded the `infratest` database with a test table.

test.sql (included)

(3) Create and grant all privileges to user `infratest` on the mysql database `infratest` with the password ‘infra1234’.

(4) Add entries to the /etc/hosts file on both servers to map the hosts `front` and `app` to their respective IP addresses

(5) Create firewall rules so that the reverse proxy server only accepts connections on port 80 from anywhere, while the app server only accepts connections on port 8080 from the proxy server.

(6) Configure nginx on the reverse proxy server to proxy HTTP requests on port 80 to the app server’s apache instance on port 8080.

(7) Configure nginx on the reverse proxy server to add the HTTP header `X- Forwarded-For` with the value of the IP address of of the client making the request.

You will provide the manifest/playbook/other config/scripts to configure each server. Running the configuration on each server will provision to these requirements. To test the accuracy of your submission, it will be run on a base centos 6 vm. Accessing nginx on front or apache on app should respond with the same results. There should be no errors on the resulting test.php page.
