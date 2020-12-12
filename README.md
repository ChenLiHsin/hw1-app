# **Cloud HW1 - Virtualization Practices**

### **Target**: Build my own application using VM && Container

> Note: When using the docker container, (1) Create my own Dockerfile (2) Build my own docker image (3) Naming with my own Student No. (4) Run a Docker container to demo your application

## **Part1 - Application on VM**   

1. Prepare the HTML file `index.html` that we want to show, for now the content is my student ID.  
      ![](https://i.imgur.com/lsEzFFo.png)

2. If we want to show our own `index.html` on the website, we need to replace the default `index.html` (Apache2 Ubuntu Default Page) with ours (Student ID)  
      ![](https://i.imgur.com/OACxvpd.png)
 
3. Then we check the network forwarding situation   
      (outside) 8080 -> 80 (inside)
      ![](https://i.imgur.com/Z2eMWFZ.png)

4. Because the host port we set is 8080, we open the website with the address `127.0.0.1:8080` or `localhost:8080`, then we see the student ID.   
    ![](https://i.imgur.com/xUxiDtR.png)


---

## **Part2 - Application on Container**   
1. First, we need to prepare the `index.html` which we want to display on the website. Meanwhile we create a new directory `./cloud_hw1`  
    ![](https://i.imgur.com/K7sYGeM.png)
 
2. Create a HTML file `index.html`  
    ![](https://i.imgur.com/99sSPJc.png)

3. Before we run the application in the container, we need to create our own **Image**, and before we create our Image, a **Dockerfile** is necessary.  
    ![](https://i.imgur.com/MgGSDMh.png)  
    
        * `FROM nginx` : I choose **nginx** to be my based image to open a HTML file.  
        * `MAINTAINER LouisChen`: To declare that this image is created by me.
        * `COPY index.html /usr/share/nginx/html`: According to the official nginx document, if we want to display `index.html` on the website, we need to put it under the directory `/usr/share/nginx/html` which exists in nginx image

4. After we create a dockerfile, we can start building our image by using the command `docker build -t 10627122 .` to build a new image with my student ID. 
      ![](https://i.imgur.com/Ih4kVzy.png)  
        
        We can check whether the new image exist by command `docker images`  
        ![](https://i.imgur.com/jSmgoTa.png)

 
5. Now the image is ready, we then create a **container** based on image **10627122** which we just built.  
     
       Use the command: `docker run -it -d -p 8000:80 --name 10627122html 10627122`  
      ![](https://i.imgur.com/D1A4YLY.png)

6. As we defined the host port with 8000, we need to check whether the port forwarding is correct.  
      ![](https://i.imgur.com/JqfpzJs.png)

7. After everything was set up, we can visit the website with IP `127.0.0.1:8000` or `localhost:8000`, then we get the Student ID.  
       ![](https://i.imgur.com/mBBUZBU.png)

---

## **Part3- Advanced practice with Container**  
  > Try to run our previous object classification project in the container
  1. First, clone our project from github and there're four files `index.html`, `transferLearning.js`, `style.css`, `README.md`   
    ![](https://i.imgur.com/4MJSOZl.png)

  2. As we done before, create a dockerfile for this application. Different with Part1 and Part2, now there two extra files that we need to copy.  
    `transferLearning.js` and `style.css`    
    ![](https://i.imgur.com/8xhoWkk.png)

  3. After dockerfile was prepared, build the image which called `advance`.  
    ![](https://i.imgur.com/6dbyZMq.png)

  4. Create a container based on **advance** image.  
    ![](https://i.imgur.com/aKclH46.png)

  5. Open the website as we done before.   
    Successfully display the HTML file which I wrote before and run the classification model correctly.   
    ![Uploading file..._digo646y1]()

## **Reference**  
  [Nginx and Mapping](https://ithelp.ithome.com.tw/articles/10199993)  
  [Introduction of docker's Network](https://ithelp.ithome.com.tw/articles/10193291)  
  [How to write Dockerfile](https://yingclin.github.io/2018/docker-basic.html)  
  [Nginx Image Introduction](https://www.docker.com/blog/how-to-use-the-official-nginx-docker-image/)  
  [Nginx Official](https://hub.docker.com/_/nginx)  