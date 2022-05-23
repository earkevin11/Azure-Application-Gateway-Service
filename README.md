# Azure-Application-Gateway-Service

# What is the purpose of Application Gateway Service?
- Service that load balances traffic at the OSI Layer 7 Application layer
- When deploying an application gateway service, admins must have an empty subnet. 
- It will be deployed on a virtual network.
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

- Create html page 

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/169736408-6539d5b6-1916-4e7d-8483-d895b58b97f2.png" height="90%" width="90%" alt="application gateway"/>

<p/>



