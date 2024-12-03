# Assignment 3 Part 2 for ACIT 2420

## Setup Instructions
Before you start the following tasks, make sure you do the following:

```sudo pacman -Syu```
This will update your system and make sure you have the latest packages.

```sudo pacman -S nginx```
This will install the nginx package.

```sudo pacman -S nvim```
This will install the nvim package.

```sudo pacman -S git```
This will install the git package.

```sudo pacman -S ufw```   
This will install the ufw package.

Then run the script by running the following command:

```chmod +x setup.sh```

```sudo ./setup.sh```

## Tasks
### Task 1: Create 2 New Digital Ocean Droplets running Arch Linux with the tag "web"

You will use this tag when you setup your load balancer.

![two new droplets](assets\two-droplets.png)

### Task 2: Create a load balancer
The load balancer should be public facing and balance traffic between the two droplets you created in Task 1.
