				 							named.conf.local

zone "sitioa.com" {
        type master;
    file "/etc/bind/rd.sitioa.com"";
};

zone "sitiob.net"{
        type master;
    file "/etc/bind/rd.sitiob.net";
};

zone "sitioc.net" {
        type master;
    file "/etc/bind/rd.sitioc.net";
};



zone "5.168.192.in-addr.arpa" {
    type master;
        file "/etc/bind/r1.192.168.5";
};
	
rd.dam1.com

											
$TTL 38400

@   IN  SOA servidor01.sitioa.com. correoadmin.sitioa.com. (
            2014092901
            28800
            3600
            604800
            38400 )

@ IN NS servidor01.sitioa.com.
servidor01.sitioa.com. IN A 192.168.5.20
www.sitioa.com. IN CNAME servidor01.sitioa.com.



$TTL 38400

@   IN  SOA servidor01.sitiob.net. correoadmin.sitiob.net. (
            2014092901
            28800
            3600
            604800
            38400 )

@ IN NS servidor01.sitiob.net.
servidor02.sitiob.net. IN A 192.168.5.21
www.sitiob.net. IN CNAME servidor01.sitiob.net.




$TTL 38400

@   IN  SOA servidor01.sitioc.net. correoadmin.sitioc.net. (
            2014092901
            28800
            3600
            604800
            38400 )

@ IN NS servidor01.sitioc.net.
servidor03.sitioc.net. IN A 192.168.5.22
www.sitioc.net. IN CNAME servidor01.sitioc.net. 


ri.192.168.5	

$TTL 38400

@   IN  SOA servidor01.sitioa.com. correoadmin.sitioa.com. (
    2014092900;  //num serie
    28800; //refresco
    3600;  //reintentos
    604800; //caducidad
        38400); // tiempo en caché

@ IN NS servidor01.
20 IN PTR servidor01.
@ IN NS servidor02.
21 IN PTR servidor02.
@ IN NS servidor03.
22 IN PTR servidor03.

nano /etc/sysctl.conf  
 
net.ipv4.ip_forward=1  
 
nano router.sh


#!/bin/bash  
iptables -t nat -A POSTROUTING -o ens33 -j MASQUERADE  
  
sh /home/usuario/router.sh  
! [raid0] (https://github.com/Jhomiu/Ejercicio/blob/master/raid0linux.JPG)
! [raid5] (https://github.com/Jhomiu/Ejercicio/blob/master/raid5linux.JPG)

