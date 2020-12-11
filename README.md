# Cloud HW1 - Virtualization Practices

### **Target**: Build my own application using VM && Container

> Note: When using the docker container, (1) Create my own Dockerfile (2) Build my own docker image (3) Naming with my own Student No. (4) Run a Docker container to demo your application

* ## **Part1-** Application on VM
    * Prepare the HTML file `index.html` that we want to show, for now the content is my student ID.  
      ![](https://i.imgur.com/lsEzFFo.png)

    * If we want to show our own `index.html` on the website, we need to replace the default `index.html` (Apache2 Ubuntu Default Page) with ours (Student ID)  
      ![](https://i.imgur.com/OACxvpd.png)
 
    * Then we check the network forwarding situation   
      (outside) 8080 -> 80 (inside)
      ![](https://i.imgur.com/Z2eMWFZ.png)

    * Because the host port we set is 8080, we open the website with the address `127.0.0.1:8080` or `localhost:8080`, then we see the student ID.   
    ![](https://i.imgur.com/xUxiDtR.png)

* ## **Part2-** Application on Container

* ## **Part3-** Advanced practice with Container

* ## Problem and solution 

* ## Reference  
  [Nginx and Mapping](https://ithelp.ithome.com.tw/articles/10199993)
  [Introduction of docker's Network](https://ithelp.ithome.com.tw/articles/10193291)
  [How to write Dockerfile](https://yingclin.github.io/2018/docker-basic.html)