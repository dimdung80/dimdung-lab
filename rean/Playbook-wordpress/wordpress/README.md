WordPress+Nginx+PHP-FPM+MariaDB Deployment
===========================================
Note: You can use below user Data while launching AWS Instances or you can run the below playbook wiht your CM Servers, Ansible Tower Or from your Local Workstation 
```
      UserData: 
        "Fn::Base64": !Sub |
          #!/bin/bash
          # Install EPEL repo for RHEL 7 
          rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm

          # Install git to clone Github repo 
          yum install git -y 

          # Install Pip packages 
          yum install python-pip -y  

          # Install Ansible after the PIP modules 
          pip install ansible

          #Set clone the git from the Github and run the playbook
          cd /tmp/ 
          git -c http.sslVerify=false clone https://github.com/dimdung80/lab-rean/
          #cd /tmp/lab-rean/workpress/
          #ansible-playbook -i hosts site.yml 
          ansible-playbook -i "localhost," -c local lab-rean/wordpress/site.yml
```
