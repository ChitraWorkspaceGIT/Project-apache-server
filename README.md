**PROJECT::Apache Web Server on a Docker container**



**1.Create an EC2 Instance**

Httpd-server

Linux machine

T2.micro

Any key pair

All tcp security group

8gb storage

**2.Connect to Mobaxterm**

Ip add of httpd-server

Ec2-user

Select keypair

***3.Install Docker on Linux machine and enable it***

```
#sudo -i

#yum install docker -y

#sudo sytemctl status docker

#sudo systemctl start docker

#sudo systemctl enable docker
```

(here docker is active and running state)

```#docker version```

***4.Create a Dockerfile and html file***

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

***5.Build the image and run the container with connector port***

```#sudo docker build -t dockerhubusername/imagename:latest .```

```#sudo docker run -itd -p 9090:80 dockerhubusername/imagename:latest```

***6.Expose the apache server***

#curl http://ipadd of httpd-server:9090/index.html 

Go to chrome browser

Paste the ipadd of httpd-server:9090

***7.Push the image to Dockerhub***

```#docker images

#sudo docker login 

#docker push dockerhubusername/imagename:latest
```
