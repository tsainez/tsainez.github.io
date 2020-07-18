---
layout: post
title:  "Hosting a Free Dedicated Minecraft Server"
date:   2020-07-18 3:18:13.68 -0700
tag: computer science
comments: true
---

This post records the process for creating and hosting a dedicated Minecraft server at no cost through the usage of student packs. 

Additionally, we won't have to port forward. This means this set up is more secure, and possibly easier to set up in the case of unknown router configurations or other special scenarios.

# Step 1: GitHub Education
If you're a student in university, there's a good chance you can get a [GitHub student pack](https://education.github.com/pack/offers), which includes $50 [Digital Ocean](https://cloud.digitalocean.com/) credit as of 18 July 2020. This can be used to create a droplet which will host our server.

1. Sign up on [GitHub](github.com) and collect a [student pack](https://education.github.com/pack/offers).
2. Sign up on [Digital Ocean](https://cloud.digitalocean.com/) and collect the $50 via the promo code provided by GitHub Education.

# Step 2: Digital Ocean sever creation
Digital Ocean is a cloud infastructure service. In our case, the service they will be providing is a host for our server. This means we won't have to port forward, and therefore this is much more secure since we go through a third party.

1. Navigate to Digital Ocean and create a new Ubuntu droplet using any plan you prefer.
	- It is advisable to keep in mind that the longevity of your server is at stake when you choose which plan.
2. Navigate to the "access" tab in the droplet and log in. This will SSH you into the server.
	- The default username is `root`, and it uses whatever password you created the droplet with.
	- It's possible to gain access to the server given password and username via any other method, such as [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/).

What you should be now looking at is an Ubuntu terminal, where you have access to the server.

# Step 3: Minecraft Server creation
Now it's time to download all the files necessary to create a server.

1. Install Java. This can be done by running `apt-get default-jre`.
	- If you encounter errors, try running any of these commands. These are what is suggested by the system. It can be helpful to read error messages —even if it takes a while to pick out what they are really saying.
		- `sudo apt-get update`
		- `sudo apt-get install --fix-missing`
		- `sudo apt-get install openjdk-6-jre-headless`
2. Run `cd /home/` to navigate to a cleaner and more manageable part of your server.
3. Run `mkdir mc` to create a folder where you can store your server and its information.
4. Run `cd mc` to go into that folder you just created.
5. Outside of your server terminal on a webrowser like Google Chrome, go to the [official Minecraft server download website](https://www.minecraft.net/en-us/download/server).
6. Copy the link to the server jar, usually by right-clicking and selecting "Copy link".
7. Go back to your server terminal. Run `wget ...` and replace the `...` with whatever the link to the server file was. 
	- If you want to copy and paste the server link, it can usually be done by right clicking, **NOT** by CTRL+V or COMMAND+V.
8. Run `java -Xmx1024M -Xms1024M -jar server.jar nogui` to run the server.
	- Notice this `server.jar` can be configured in many different ways to suit the needs of your specific set up.

You should now be running a dedicated Minecraft server! Use the IP address of the droplet to connect, and have fun!

Be aware this setup can easily crash without additional processing power, so this application is very niche. However, hopefully through this tutorial you will have learned a little bit about Linux, terminals (bash) and servers.