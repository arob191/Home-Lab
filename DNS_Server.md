Steps I took to setup my DNS server
  -First I setup an old intel nuc as a small server for my network by leaving it on and giving it a static IP address
  -I then installed docker desktop on my server
  -Using powershell I downloaded the Pi-hole image and used a custom script to start it
  -I asigned DNS 1 to the localhost 127.17.0.1
  -Lastly after the Pi-hole was running I went into my router and changed the DNS settings to point to my server