The automation is used to deploy spring petclinic rest application into AWS cloud.

To spin up the required infrastructure in AWS cloud refer https://github.com/kmanvitha30/terraform-petclinic


## Pre-Requisities:
The machine from which the automation script is executed should have git installed. Requires maven/docker/helm based on the installation method.
```
#git
sudo yum install git -y
git --version

#maven
sudo yum install maven -y
mvn --version

#docker
sudo yum install docker -y
sudo systemctl start docker
sudo systemctl enable docker
docker -v

#helm
```
wget -O helm.tar.gz https://get.helm.sh/helm-v3.5.4-linux-amd64.tar.gz
tar -zxvf helm.tar.gz
sudo mv linux-amd64/helm /usr/local/bin/helm
helm version
```

## To Run Locally:
1. Clone the git repository and make petclinic-rest as the current working directory.
```
git clone https://github.com/kmanvitha30/petclinic-rest.git
cd petclinic-rest/
```

2. Run with maven command line:
```
cd docker/
./mvnw spring-boot:run
```

3. Run with Docker:
```
cd docker/
docker build -t <docker_repository>/petclinic-rest:<image_tag> .
docker run -p 9966:9966 <docker_repository>/petclinic-rest:<image_tag>
```

4. With helm:
```
helm install <release_name> helm-petclinic_rest
NOTE : Update the values.yaml prior running.
```

5. The application can be accessed at:
```
http://<endpoint-address>:9966/petclinic/swagger-ui.html
```