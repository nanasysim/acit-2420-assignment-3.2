# Assignment 3 Part 2 for ACIT 2420

## Tasks
### Task 1: Create 2 New Digital Ocean Droplets running Arch Linux with the tag "web"

You will use this tag when you setup your load balancer.

It should look something like this:  
![two new droplets](assets/two-droplets.png)

### Task 2: Create a load balancer
The load balancer should be public facing and balance traffic between the two droplets you created in Task 1.

Settings for the load balancer:
* Regional, SFO3, same as your servers
* Default VPC, same as your servers
* External(public)
* Use the "web" tag to load balance all servers with a web tag in the SF03 region

It should look something like this:  
![load-balancer](assets/load-balancer.png)

### Task 3: Clone the starter code

Clone the starter code from the following repository:
https://git.sr.ht/~nathan_climbs/2420-as3-p2-start

This can be done by running the following command on your terminal:

```
git clone https://git.sr.ht/~nathan_climbs/2420-as3-p2-start
```

### Task 4: