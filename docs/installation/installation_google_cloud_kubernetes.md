## Installing Yacy on Google Cloud with Docker


1. Go to [Google Cloud Free Trial](https://cloud.google.com/free-trial/) and sign up. You will get 300 dollars credit for 12 months.


2. Go to the console page: [Console](https://console.cloud.google.com/home)


3. If you don’t have any projects, a page that would guide you on how to start a project will pop up. Give your project a name.


4. In the search bar above on console page, enter 'Compute Engine' and click on ```Compute Engine```. 


5. If you have not activated billing for compute engine, click enable billing and choose your account to activate your Compute Engine. Your Google Compute Engine should be activated within a few minutes.


6. Click ```Create instance``` to create an instance. In machine type, choose ```small(1 shared vCPU)```.
	Choose whatever zone you like.
 
	In Boot Disk, choose ```Ubuntu 14.04```, and the disk size should be larger than 40GB.
	On the bottom of the page, click ```Management, disk, networking, access & security options``` to show more options. Inside of this, click into the tab ```Networking``` and choose ```New static IP``` instead of ```Ephemeral```. Enter a name for your IP. Google will assign a IP for you.
	Check the two boxes ```Allow HTTP traffic``` and ```Allow HTTPS traffic```. Finally, click ```Create``` to create an instance. Wait a few minutes for the creation to complete.


7. Once the creation has finished, click ssh below to establish web ssh connections.

8. In the Web Console, enter:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get -y install docker.io
sudo fallocate -l 4G /swapfile
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
sudo docker pull nikhilrayaprolu/yacy_grid_mcp
```

Once finished, you will get fully working image. You can check if it exists by entering ```sudo docker images```.
Run our server by entering:
```
sudo docker run -d -p 8100:8100 -p 443:443 nikhilrayaprolu/yacy_grid_mcp
```
Enter your assigned HTTP IP address into your browser to check if it is working.
