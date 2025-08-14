**🐳 Apache Web Server on Docker Container (AWS EC2 Deployment)**

This project demonstrates deploying an Apache HTTP Server inside a Docker container hosted on an AWS EC2 instance. The setup includes:

Building a custom Docker image with Apache

Hosting a sample HTML page

Exposing it on a public port

Pushing the image to Docker Hub

**🔹 Project Steps
1️⃣ Create an EC2 Instance**

Type: t2.micro

OS: Amazon Linux

Storage: 8 GB

Security Group: All TCP (for testing)

Key Pair: Any existing or new key pair

Name: httpd-server

**2️⃣ Connect to EC2 (MobaXterm / SSH)**

```ssh -i keypair.pem ec2-user@<EC2-IP>```

Ip add of httpd-server

Ec2-user

Select keypair

***3️⃣ Install & Enable Docker***

```
#sudo -i

#yum install docker -y

#sudo sytemctl status docker

#sudo systemctl start docker

#sudo systemctl enable docker
```

(here docker is active and running state)

```#docker version```

***4️⃣ Create Dockerfile & HTML***

#vim dockerfile 

```FROM ubuntu

RUN apt update

RUN apt install apache2 -y

RUN apt install apache2-utils -y

RUN apt clean

COPY /sourcecode/ /var/www/html/

EXPOSE 80

ENTRYPOINT ["apache2ctl"]

CMD ["-DFOREGROUND"]
```

#ls

#sudo mkdir sourcecode

#cd sourcecode

#Vi index.html

```<h3>welcome to my world</h3>```

#cd..

***5️⃣ Build the image and run the container with connector port***

```
#sudo docker build -t dockerhubusername/imagename:latest .

#sudo docker run -itd -p 9090:80 dockerhubusername/imagename:latest
```
***6️⃣ Expose the apache server***

```#curl http://ipadd of httpd-server:9090/index.html ```

Go to chrome browser

Paste the ipadd of httpd-server:9090

***7️⃣ Push the image to Dockerhub***

```#docker images

#sudo docker login 

#docker push dockerhubusername/imagename:latest
```
🔹 Key Highlights

✅ Apache server in Docker container hosted on AWS EC2

✅ Custom image with HTML content

✅ Port mapping for external access

✅ Image pushed to Docker Hub
