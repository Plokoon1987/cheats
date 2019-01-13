Follow instructions in /etc/dhcpcd.conf

Login as sudoer:

In terminal (example only):
  sudo nano /etc/dhcpcd.conf:

    # fallback to static profile on eth0
    #interface eth0
    #fallback static_eth0
    '
    '
    '
    #static IP configuration
    interface eth0
        static ip_address=192.168.1.XX/24
        static routers=192.168.1.1
        static domain_name_servers=192.168.1.1 8.8.8.8
    interface wlan0
        static ip_address=192.168.1.XX/24
        static routers=192.168.1.1
        static domain_name_servers=192.168.1.1 8.8.8.8
