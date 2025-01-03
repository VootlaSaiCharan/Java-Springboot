## Sonarqube Installation:

yum install unzip

adduser sonarqube

passwd sonarqube

su - sonarqube

wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-9.4.0.54424.zip

unzip *

chmod -R 755 /home/sonarqube/sonarqube-9.4.0.54424

chown -R sonarqube:sonarqube /home/sonarqube/sonarqube-9.4.0.54424

cd sonarqube-9.4.0.54424/bin/linux-x86-64/

./sonar.sh start


## Trivy Installation Steps

sudo apt-get install wget apt-transport-https gnupg lsb-release

wget -qO - https://aquasecurity.github.io/trivy-repo/deb/public.key | sudo apt-key add -

echo deb https://aquasecurity.github.io/trivy-repo/deb $(lsb_release -sc) main | sudo tee -a /etc/apt/sources.list.d/trivy.list

sudo apt-get update -y

sudo apt-get install trivy -y

## To install json 
sudo apt-get install jq -y

## trivy Commands

trivy image imagename

trivy fs --security-checks vuln --severity HIGH,CRITICAL Folder_name_OR_Path

trivy image --severity HIGH,CRITICAL image_name    

you can use --severity (LOW,MEDIUM,HIGH,CRITICAL) 

trivy image -f json -o results.json image_name

trivy repo repo-url

trivy k8s --report summary cluster


example
```bash
trivy fs --security-checks vuln --severity HIGH,CRITICAL Folder_name_OR_Path
trivy image --security-checks vuln --severity HIGH,CRITICAL -f table -o Image_Scan.html image_name
```



