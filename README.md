# Azure-Application-Gateway-Service

# What is the purpose of Application Gateway Service?
- App gateway is a web traffic load balances service that load balances traffic at the OSI Layer 7 Application layer
- Azure application gateway routes the traffic/request based on the URL.
- Application gateway managed SSL for users. 
- Communicaton from client to the app gateway is secure because of SSL
- Admins can enable Autoscaling and the Web Application Firewall


# How would users access the Azure Application Gateway?
- There is a frontend IP address where users will use

# An EMPTY subnet will need to be created for the Application Gateway machines.
- These application gateway machines will be in charge of routing traffic to the machines in the backend pool.
- Users will not be able to create an application gateway within a used subnet. It must be empty.


# How to create an additional subnet within the Virtual Network?
- Virtual network > subnets > add an additional subnet for the application gateway instances


# How to configure Azure Application Gateways?
- Users will need to configure three parts:
- Frontend
- Route Rules
- Backend Pool


# Use Case: Use an application gateway to route user's request to image and video server
- Two VMs where appvm1 is the image server and appvm2 is the video server
- Application gateway needs to route the traffic to each server based on user's request

# Both servers must have HTTP port open

# appvm1 configuration

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/169735527-9fa39528-2a93-4828-8503-0ee5822f356b.png" height="100%" width="100%" alt="application gateway"/>

<p/>

# appvm2 configuration

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/169735564-82a479ca-7f59-4090-b6a4-8ce0e39c3de0.png" height="100%" width="100%" alt="application gateway"/>

<p/>


# Set up IIS Web Server for both servers and add an image file and video file

- Add roles and features > Select Web Server IIS


<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/169736408-6539d5b6-1916-4e7d-8483-d895b58b97f2.png" height="90%" width="90%" alt="application gateway"/>

<p/>

- Create html page for image server
- Users will have to open up notebad and add html code 
- Save it has a webpage by selecting UTF-8 and all documents

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/169743328-85b2e0b3-42e9-42af-8fc3-5dc6b7af925b.png" height="90%" width="90%" alt="application gateway"/>

<p/>


- Create html page for video server
- Users will have to open up notebad and add html code 
- Save it has a webpage by selecting UTF-8 and all documents

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/169743396-a6999e61-7775-4de6-8529-e3a24710dbf1.png" height="90%" width="90%" alt="application gateway"/>

<p/>

- Enter the public IP address of appvm1 / folder name / page name with .html 
- This page should show up

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/169743837-dcd9a672-c468-476a-8cfd-2ea9c1b87197.png" height="90%" width="90%" alt="application gateway"/>

<p/>


- Enter the public IP address of appvm2 / folder name / page name with .html 
- This page should show up

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/169743894-cab3095c-76b1-474b-8273-b849b3f73373.png" height="90%" width="90%" alt="application gateway"/>

<p/>


# How to implement Application Gateways?
- Add an empty subnet for the application gateway instances

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/169744174-23f388d0-7833-496d-9622-85bdf8368ee3.png" height="190%" width="190%" alt="application gateway"/>

<p/>


- Create the application gateway and add into the empty subnet that was created
- Remember, that application gateway intances need an empty subnet.

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/169745089-5dc8411b-e371-4c29-a084-6984e32ef769.png" height="190%" width="190%" alt="application gateway"/>

<p/>

- Add a public IP

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/169745136-aef57a42-f015-4364-9948-2df185472453.png
" height="190%" width="190%" alt="application gateway"/>

<p/>


- Add backend pools of imagespool 
- Configure image pool to link with appvm1 

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/169745183-1f2fd79d-3c89-4607-956f-1479e7830c65.png" height="300%" width="300%" alt="application gateway"/>

<p/>

- Add backend pools videospool
- Configure video pool to link with appvm2 since that is where the video server is 

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/169745254-0dcebef8-18ea-4c99-ae2e-ae06ea7d927c.png" height="300%" width="300%" alt="application gateway"/>

<p/>


- Add routing rules
- These rules will direct frontends to backends.


# Backend targets
- Set a rule name and priority
- Select backendpool
- Use the default backend settings
- Users will need to add path based rules


# Important that path names is the same as the folder name that was created

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/169746630-6f5a5eb9-f626-4705-8aea-78b952b5297e.png" height="100%" width="100%" alt="application gateway"/>

<p/>

# Important that path names is the same as the folder name that was created
# Create the rule and add it

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/169746681-1809657d-5ef4-49f0-b473-dc6625b94d3d.png" height="100%" width="100%" alt="application gateway"/>

<p/>


# Test it out by accessing the front-end IP of the application gateway 
- Remember to use the public IP of each VM and use the path names 
- Enter the public IP address of appvm1 / folder name / page name with .html 
- Here users can see the application gateway working as it directs traffic

# Front-end IP of app gateway
- IP is what users will access: 20.211.173.158

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/169747592-c7ccb252-70a3-4446-b5c5-3763b4c78b9c.png" height="100%" width="100%" alt="application gateway"/>

<p/>

# Image server
- http://20.211.173.158/images/image.html

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/169747883-0d048f28-a5b5-44e3-87a9-6b4ff1225c5b.png" height="100%" width="100%" alt="application gateway"/>

<p/>


# Video server
- http://20.211.173.158/videos/video.html
<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/169747920-f7272be8-1f6f-4c34-a19f-3b926b88c474.png" height="100%" width="100%" alt="application gateway"/>

<p/>
