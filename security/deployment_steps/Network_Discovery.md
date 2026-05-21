

Host Discovery scans are [low impact](https://www.tenable.com/blog/using-nessus-for-host-discovery) and should not cause any 
issues for the network during use. Even so, we will run a very basic Ping-Only Discovery with the Scan 
low bandwitdh links option. Most devices running local applications allow for pings from internal 
network only to help with troubleshooting and should be detected by this scan. If I was doing a
more indepth scan for penetration testing, vulnerability scanning, or asset discovery then I would/will
switch to different options as most devices be default will auto block ping/ICMP requests. 
