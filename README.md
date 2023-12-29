# Just some old and maybe useful linux commands

## Transfer files through each vps:

>scp -r -P port root@ip:/root/* .

then

>scp -r -P port root@ip:/usr/lib/libcxa.so.1 /usr/lib/libcxa.so.1



## Update VPS OS:

>apt-get update && apt-get -y upgrade && apt-get -y dist-upgrade



## check services

>ps aux

or

>man top



## hosting jedi academy server:

>cd jka
>
>chmod +x linuxjampded
>
>apt-get install screen
>
>screen -dm ./linuxjampded +set net_port +exec server.cfg





## VERTEX on Proton Linux

>apt-get install winetricks
>
>apt-get install protontricks
>
>winetricks --self-update
>
>winetricks appid vcrun2019





## no-internet access on application

>sudo addgroup no-internet  # Create group "no-internet"
>
>sudo adduser $USER no-internet  # Add current user to no-internet



>sudo iptables -I OUTPUT 1 -m owner --gid-owner no-internet -j DROP
>
>sudo ip6tables -I OUTPUT 1 -m owner --gid-owner no-internet -j DROP # To also block IPv6 traffic


>sg no-internet -c "processFullPath args"



## wine related commands

### Setting the language wine uses

>LANG=ja_JP.UTF-8 wine /path/to/game/game.exe

### Start wine with a prefix

>WINEPREFIX=/home/alex/.local/share/wineprefixes/wine64/ wine start /unix


## Linux TDP limiting/undervolt

>sudo nvidia-smi -pm 1  
>sudo nvidia-smi -i 0 -pl 180  
>sudo nvidia-smi -i 0 -lgc 1500,1600

### if get warning "Setting locked GPU clocks is not supported for GPU" try:
>nvidia-settings -c :0 -a '[gpu:0]/GPUGraphicsClockOffset[3]=-200'

>nvidia-settings -c :0 -a '[gpu:0]/GPUGraphicsClockOffset[2]=-250'

>nvidia-settings -c :0 -a '[gpu:0]/GPUGraphicsClockOffset[1]=-300'


## OLD

### Proton-call lets you play game via proton that is not just on Steam
proton-call -p experimental -r game.exe

TS3 Server:

>cd ts3server
>
>./ts3server_minimal_runscript.sh default_voice_port=21805 query_port=21805 query_ip=192.168.12.218 filetransfer_port=21807 filetransfer_ip=192.168.12.218 &



Compile OpenRP mod for JA:

>apt-get install git build-essential cmake
>
>git clone
>
>cd openRP
>
>cmake -G "Unix Makefiles" ..
>
>make



Install webserver:

>apt-get update && apt-get -y install apache2 mysql-server php5-cli

change apache port to forwarded port

edit index page @ /var/www/index.html

>nano /etc/apache2/apache2.conf

change Listen 80 line to diff port

>nano /var/www/index.html

to disable: 
>service apache2 stop
>service mysql-server stop



OpenVPN script:

>wget https://raw.github.com/cwaffles/ezopenvpn/master/ezopenvpn.sh --no-check-certificate -O ezopenvpn.sh; chmod +x ezopenvpn.sh; ./ezopenvpn.sh
