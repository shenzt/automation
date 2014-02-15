Automation
==========

The details of BBB board

http://elinux.org/Beagleboard:BeagleBoneBlack

Download the latest Ubuntu image from

http://elinux.org/BeagleBoardDebian#eMMC:_BeagleBone_Black

Holding down the boot button, apply power to the board. Continue to hold boot botton until USER LEDs begin to flash

### Expanding the file system partition

http://elinux.org/Beagleboard:Expanding_File_System_Partition_On_A_microSD


### Setup WIFI Connection 

Add the following settings to `/etc/network/interfaces`

    auto wlan0
    iface wlan0 inet dhcp
        wpa-ssid "SSID"
        wpa-psk "password"

### Change time zone

    sudo mv /etc/localtime /etc/localtime-utc
    sudo ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime

### Change your hostname

    nano /etc/hostname

### Create a new user

    sudo adduser shenzt
    adduser shenzt sudo # Make it sudo user

### Disable apache2
    
    update-rc.d apache2 disable 

### Setup Python environment

    apt-get install python-pip
    sudo pip install xively-python --pre
    sudo pip install pyserial
    sudo pip install psycopg2

### Setup PostgreSQL

    sudo apt-get install postgresql postgresql-server-dev python-psycopg2 

edit `/etc/postgresql/9.1/main/pg_hba.conf` with the following lines.

    local   all             postgres                                trust
    local   all             automation                              trust

### Misc 

    apt-get install curl



