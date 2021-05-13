# TASK-1_MLOPS-DEVOPS

###### Machine Learning integrated with devops.</br>

###### Task Description:</br>
JOB#1 If Developer push to dev branch then Jenkins will fetch from dev and deploy on dev-docker environment.</br>

JOB#2 If Developer push to master branch then Jenkins will fetch from master and deploy on master-docker environment. both dev-docker and master-docker environment are on different docker containers.

JOB#3 Manually the QA team will check (test) for the website running in dev-docker environment. If it is running fine then Jenkins will merge the dev branch to master branch and trigger #job2
________________________________________________________________________________________

HERE WE START THE TASK.....(●'◡'●)

Firstly create a github repository consisting of files.

W can either make repository using git bash from desktop or straight forward do it in it's website!

We'll change ourself from 'main' branch to 'master' branch

![image](https://user-images.githubusercontent.com/64470404/118102215-217b7d80-b3f6-11eb-90cd-ae76a396a880.png)
-----------------------------

From here we can change ourselves to any of the branch in my case it is as shown below:
![image](https://user-images.githubusercontent.com/64470404/118102340-4c65d180-b3f6-11eb-89ff-8f664b68ddf1.png)
----------------------------

And now we'll shift to master branch and there we'll commit a new file:

![image](https://user-images.githubusercontent.com/64470404/118102480-7b7c4300-b3f6-11eb-882e-03530166e15c.png)
---------------------------

![image](https://user-images.githubusercontent.com/64470404/118102526-89ca5f00-b3f6-11eb-9eea-3b6d299a6de3.png)
-----------------------------

And now we'll shift to dev branch and commit a file there as shown below!

![image](https://user-images.githubusercontent.com/64470404/118102558-964eb780-b3f6-11eb-9cf3-ab2575433db3.png)

-------------------------
![image](https://user-images.githubusercontent.com/64470404/118102653-b1212c00-b3f6-11eb-9b32-2881131e6100.png)

![image](https://user-images.githubusercontent.com/64470404/118102677-b67e7680-b3f6-11eb-8e28-f63c00e8dac2.png)

-----------
Now the next part comes up here is of jenkins
we'll setup jenkins first in our system (can refer to this if you haven't: https://github.com/RK1905101/Jenkins_Setup)

Open your Linus system and give power to jenkins 
go to the following folder and write the following:
```
gedit /etc/sudeors

jenkins ALL=(ALL)  NOPASSWD: ALL
```
![image](https://user-images.githubusercontent.com/64470404/117955131-570c6200-b335-11eb-9b8d-420da9d654c4.png)

![image](https://user-images.githubusercontent.com/64470404/118101842-aca84380-b3f5-11eb-857c-6eb2109fd425.png)

-----------

Now open jenkins and create first job so as to perform the task!

Select "NEW ITEMS" from left panel of the page so as to create a new job.

![image](https://user-images.githubusercontent.com/64470404/118102907-f9404e80-b3f6-11eb-8b02-72f623dd9640.png)

Now enter the name of your task and select "freestyle project" and then click ok.
In my case it is "Test" 
![image](https://user-images.githubusercontent.com/64470404/118103629-c0ed4000-b3f7-11eb-92d1-e26d410fddb7.png)

Now from here onwards your project description starts:

enter your github project repository url here:

![image](https://user-images.githubusercontent.com/64470404/118104205-75876180-b3f8-11eb-89e5-830a616c168e.png)

![image](https://user-images.githubusercontent.com/64470404/118104240-82a45080-b3f8-11eb-9a36-72f9755a189c.png)

Now go down and click on "ADD BUILD STEP" inside BUILD
Choose "execute shell" and then write the following:
```
sudo  cp -vrf * /root/mastergit

if 
sudo docker ps | grep mastergit
then
echo ""Mastergit is Already Running"
else
sudo docker run -dit -p 8082:80 -v /root/mastergit:/usr/local/apache2/htdocs/ --name mastergit httpd
fi

sudo cp -vrf * /root/devgit

if sudo docker ps | grep devgit
then
echo "Devgit is already running"
else
sudo docker run -dit -p 8081:80 -v /root/devgit:/usr/local/apache2/htdocs/ --name devgit httpd
fi

echo "success"
```
![image](https://user-images.githubusercontent.com/64470404/118104363-acf60e00-b3f8-11eb-974f-2b3774478e67.png)

Now click on apply and save

And then just save that!

It'll show up like this:

![image](https://user-images.githubusercontent.com/64470404/118104459-cbf4a000-b3f8-11eb-9781-1e0bc1cb1659.png)

It's console output is shown like this with success rate
![image](https://user-images.githubusercontent.com/64470404/118104608-f8102100-b3f8-11eb-8d53-a35a21a4a63c.png)
![image](https://user-images.githubusercontent.com/64470404/118104625-fe9e9880-b3f8-11eb-9f8d-a132fc9fed27.png)

And now when we check our linux system, there are two containers created as shown below:
![image](https://user-images.githubusercontent.com/64470404/118104720-1e35c100-b3f9-11eb-9294-d2522e8b2ab2.png)

and when we open it up linux server's ip with the port number specified, we see the webpage which lands us to master of github
![image](https://user-images.githubusercontent.com/64470404/118104825-42919d80-b3f9-11eb-8d7c-7dc07e2deb00.png)

opening it up we see the message/code written there!
![image](https://user-images.githubusercontent.com/64470404/118104873-53421380-b3f9-11eb-841c-1b8439f51de0.png)

--------------------

Well that was all in the task!
Thanks!



