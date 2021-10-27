The automation is used to deploy spring petclinic rest application into AWS cloud.

To spin up the required infrastructure in AWS cloud refer https://github.com/kmanvitha30/terraform-petclinic


## Pre-Requisities:
The machine from which the automation script is executed should have git and maven installed.
```
sudo yum install git
git --version

sudo yum install maven
mvn --version
```

## To Run Locally:
1. Clone the git repository  
```
git clone https://github.com/kmanvitha30/petclinic-rest.git
```

2. Run with maven command line:
```
cd terraform-petclinic/docker
./mvnw spring-boot:run
```

3. Run with Docker:
```
cd terraform-petclinic/docker
docker build -t <docker_repository>/petclinic-rest:<image_tag> .
```

4. With helm:
```
cd terraform-petclinic
helm install <release_name> helm-petclinic_rest
NOTE : Update the values.yaml prior running.
```

5. The application can be accessed at:
```
http://<endpoint-address>:9966/petclinic/swagger-ui.html
```