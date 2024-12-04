# Assignment 3 Part 2 for ACIT 2420

## Tasks
### Task 1: Create 2 New Digital Ocean Droplets running Arch Linux with the tag "web"

You will use this tag when you setup your load balancer.

It should look something like this:  
![two new droplets](assets/two-droplets.png)

### Within you droplet, do the following:
1. Update your system by running the following command:
    ```
    sudo pacman -Syu
    ```
    This will update your system and make sure you have the latest packages.
2. Install the following packages:
    * nginx
    * nvim
    * git
    * ufw
    ```
    sudo pacman -S nginx nvim git ufw
    ```
    To check if these packages have been installed, run the following commands:  

    ```
    nginx --version
    ```
    ```
    nvim --version
    ```
    ```
    git --version
    ```
    ```
    ufw --version
    ```
### Task 2: Create a load balancer
The load balancer should be public facing and balance traffic between the two droplets you created in Task 1.

Settings for the load balancer:
* Regional, SFO3, same as your servers
* Default VPC, same as your servers
* External(public)
* Use the "web" tag to load balance all servers with a web tag in the SF03 region

It should look something like this:  
![load-balancer](assets/load-balancer.png)

>**QUESTION:**
>What is the purpose of a load balancer?  
> **ANSWER:**  
> A load balancer distributes incoming network traffic across multiple servers to ensure no single server becomes overwhelmed. This helps improve the availability and reliability of your application by balancing the load, preventing server overload, and ensuring better performance and redundancy.
### Task 3: Clone the starter code

Clone the starter code from the following repository:
https://git.sr.ht/~nathan_climbs/2420-as3-p2-start

This can be done by running the following command on your terminal:

```
git clone https://git.sr.ht/~nathan_climbs/2420-as3-p2-start
```

This contains a script that will generate an HTML document.

Then run the following command to move the generate_index script to the bin directory. Make sure generate_index is in your pwd:

```
mv generate_index /var/lib/webgen/bin/
```

>[!NOTE] 
>Alternatively, you can run the setup script. It will setup the necessary nginx configurations for the server and clone the repository for you.

#### To run the setup script
1. Make the setup file executable by running the following command:
    ```
    chmod +x setup
    ```
2. Run the setup script by running the following command:
    ```
    sudo ./setup
    ```
>[!NOTE]
Do the same thing for nginx-setup as well.

### Task 4: Update your server configuration to include a file server. 

When you visit 'your-ip/documents' you will see a list of the documents in the documents directory.

The directory structure should look like this:
```
├── bin/
│   └── generate_index
├── documents/
│   ├── file-one
│   └── file-two
└── HTML/
    └── index.html
```
This will be created in the setup script.

**Some notes:**
* index.html is still generated by generate_index
* file-one and file-two are just sample files
  * they should contain some text so that you can confirm that you can download from your file server

Both Servers should have the following features:
* updated script to generate an updated HTML document
* file server that will serve some test files on both servers.


## FOR THE VIDEO
1. Why do we make a system user?
- The goal is to isolate resources from other users.
- Creating a system user and giving ownership to the file server ensures that other users cannot access or modify the files.
- The system user does not have a login, which ensures that no one can log in and change the files.

2. Why do we make a service file?
- A service file is created to define and manage a service in a consistent and standardized way.
- It allows the service to be controlled by the system's init system (such as systemd), enabling it to start, stop, restart, and manage the service automatically.
- Service files specify how and when the service should run, including dependencies, environment variables, and execution commands.
- This ensures that the service runs reliably and can be easily managed and monitored.
- In this case, the service file is used to run the generate_index script, which generates an HTML document.

3. What is an after? wants? in a service file 
- `After` specifies the units that must be started before the service is started.
- `Wants` specifies the units that the service requires to be started but does not depend on.
- These directives ensure that the service is started in the correct order and that all dependencies are met.

4. What is a target? 
- A target is a unit that is used to group other units together
- Group of service file that achieves a specific state after it has been started

5. What is a timer?
- A timer is a unit that activates and deactivates other units based on a schedule.
  
6. What is OnCalendar? 
- `OnCalendar` specifies when the timer should activate the unit.

7. What is WantedBy?
- `WantedBy` specifies the target unit that the timer should be activated by.
8. How does this timer know what service to start?
- The timer is associated with a service by specifying the service in the `Unit` section of the timer file.