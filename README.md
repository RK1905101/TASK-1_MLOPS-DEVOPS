# TASK-1_MLOPS-DEVOPS

Giving complete power to jenkins in redhat linux.


![image](https://user-images.githubusercontent.com/64470404/117955131-570c6200-b335-11eb-9b8d-420da9d654c4.png)

![image](https://user-images.githubusercontent.com/64470404/117955048-41973800-b335-11eb-953d-b2ba58a6147f.png)

now creating git repository!
 firstly create master branch as shown below!
 
 
 and now i created 'dev' branch and uploaded files in it!

now moving down to jenkins:

creating a new job named as job1 and create a free style project
now write your github repository url in the area of source code management

![image](https://user-images.githubusercontent.com/64470404/117956057-4f998880-b336-11eb-99d1-a2a6900d6deb.png)

now add  poll scm in build triggers so that our job can be checked in every minutes, and whenever someone pushes any file or does any types of changes  then it'll specify us!
![image](https://user-images.githubusercontent.com/64470404/117956679-e8300880-b336-11eb-91ef-8263a7e13905.png)

![image](https://user-images.githubusercontent.com/64470404/117956841-0c8be500-b337-11eb-8eea-9435f2d5506d.png)

now just apply this and save it!

now create anither new job named as job2
![image](https://user-images.githubusercontent.com/64470404/117957303-8de37780-b337-11eb-87e3-70e5da63f2ea.png)

now in the 'build' section write the following:

![image](https://user-images.githubusercontent.com/64470404/117957915-24179d80-b338-11eb-9234-8d87ffeba51b.png)

if sudo docker ps | grep job1
then
echo "Already running"
else
sudo docker run -dit -p 8082:80 -v /root/job1:/usr/local/apache2/htdocs/ --name job1 httpd
fi

apply n save

now create a new job named as job3

![image](https://user-images.githubusercontent.com/64470404/117958292-807abd00-b338-11eb-953c-4f714d6f650c.png)

![image](https://user-images.githubusercontent.com/64470404/117958414-9b4d3180-b338-11eb-9a90-1b9e531dbe2a.png)




