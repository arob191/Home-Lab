This repository outlines what I have done for my home lab

My original network when I first moved in to my house was the ISP standard equipment.

Setting Up Custom Router

    -The first thing I wanted to do is setup my own router
    -I was able to salvage an old optiplex and get it working again
    -After installing a new SSD I loaded Opnsense Router OS on the drive

ISP Equipment Bridgemode
    
    -After Opensense router was successfully setup I needed to turn my current isp device into bridge mode
    -First I needed to designate my custom router as the new WAN device using the mac address
    -Next I disabled the firewall/NAT for my ISP router
    -I plugged my computer into the LAN port on my custom router and sure enough DHCP was handled properly and I had internet access

Setting Up Unifi Switch & Access Point
    
    -Since I only had a dual port NIC on my custom router I needed a switch
    -I got a used Unifi switch that also had 2 SFP ports as a bonus
    -The switch had POE capabilities which was nice since I did not need to use a POE injector for my Unifi AP
    -Within my router I needed to create the interface that the switch would use and designate it as my LAN
    -I Used cloudflare as my DNS server (1.1.1.1 & 1.0.0.1)
    -Once I had the unifi switch and ap plugged into my router I used my computer to adopt the two unifi device into my Unifi controller
    -I setup my 

Creating Vlan
    
    -First I need to go to my VLAN settings and create a new VLAN and I used the physical LAN interface as the parent interface
    -VLAN tag 2 was assigned
    -DHCP was setup for IVP4
    -The inteface was enabled
    -Firewall rules were established to allow the IPv4 and 6 taffic to flow over the interface
    -Next the VLAN was created on the Unifi switch tag 2
    -A new wireless network was then created that utilized the VLAN network.

Steps I took to setup my DNS server
    
    -First I setup an old intel nuc as a small server for my network by leaving it on and giving it a static IP address
    -I then installed docker desktop on my server
    -Using powershell I downloaded the Pi-hole image and used a custom script to start it
    -I asigned DNS 1 to the localhost 127.17.0.1
    -Lastly after the Pi-hole was running I went into my router and changed the DNS settings to point to my server.
