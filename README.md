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
! [raid0linux] (https://github.com/Jhomiu/Ejercicio/blob/master/raid0linux.JPG)
! [raid5linux] (https://github.com/Jhomiu/Ejercicio/blob/master/raid5linux.JPG)

//////////////////////////////////////////////////////////////////////////////////////////////
Siguiente ejercicio
//////////////////////////////////////////////////////////////////////////////////////////////




`sudo nano /etc/network/interfaces`
  ~~~
  # This file describes the network interfaces available on your system
  # and how to activate them. For more information, see interfaces(5).

  #source /etc/network/interfaces.d/*

  # The loopback network interface
  auto lo
  iface lo inet loopback

  # The primary network interface
  auto enp0s3
  #iface enp0s3 inet dhcp
  iface enp0s3 inet static
        address 192.168.1.210
        netmask 255.255.255.0
        gateway 192.168.1.254
        dns-nameservers 192.168.1.210
  ~~~

  `sudo service networking restart`  
  `sudo /etc/init.d/networking restart`  
  `sudo reboot`  


    `sudo apt-get install bind9`


    `sudo nano /etc/bind/named.conf.local`  
   
      ~~~
      //
      // Do any local configuration here
      //

      // Consider adding the 1918 zones here, if they are not used in your
      // organization
      //include "/etc/bind/zones.rfc1918";

      zone "gato.com"{
            type master;
            file "/etc/bind/rd.gato.com";
      };

      zone "mosquito.com"{
            type master;
            file "/etc/bind/rd.mosquito.com";
      };

      zone "escherichiacoli.es"{
            type master;
            file "/etc/bind/rd.escherichiacoli.es";
      };

      zone "chip555.org"{
            type master;
            file "/etc/bind/rd.chip555.org";
      };

 

      zone "1.168.192.in-addr.arpa"{
            type master;
            file "/etc/bind/ri.192.168.1";
      };
      ~~~

    `sudo nano /etc/bind/rd.gato.com`  
    
      ~~~
      $TTL 38400

      @ IN SOA servidor01.gato.com. correoadmin.gato.com. (
              2017041000;   //num serie
              28800;        //refresco
              3600;         //reintentos
              604800;       //caducidad
              38400);       // tiempo en caché

      @ IN NS servidor01.gato.com.
      servidor01.gato.com. IN A 192.168.1.210
      WWW IN CNAME servidor01.gato.com.
      ~~~


    `sudo nano /etc/bind/rd.mosquito.com`  
    Con la siguiente configuracion:  
      ~~~
      $TTL 38400

      @ IN SOA servidor01.mosquito.com. correoadmin.mosquito.com. (
              2017041000;   //num serie
              28800;        //refresco
              3600;         //reintentos
              604800;       //caducidad
              38400);       // tiempo en caché

      @ IN NS servidor01.mosquito.com.
      servidor01.mosquito.com. IN A 192.168.1.210
      WWW IN CNAME servidor01.mosquito.com.
      ~~~

  
      `sudo nano /etc/bind/rd.escherichiacoli.es`  
      Con la siguiente configuracion:  
        ~~~
        $TTL 38400

        @ IN SOA servidor01.escherichiacoli.es. correoadmin.escherichiacoli.es. (
                2017041000;   //num serie
                28800;        //refresco
                3600;         //reintentos
                604800;       //caducidad
                38400);       // tiempo en caché

        @ IN NS servidor01.escherichiacoli.es.
        servidor01.escherichiacoli.es. IN A 192.168.1.210
        WWW IN CNAME servidor01.escherichiacoli.es.
        ~~~


      `sudo nano /etc/bind/rd.chip555.org`  
      Con la siguiente configuracion:  
        ~~~
        $TTL 38400

        @ IN SOA servidor01.chip555.org. correoadmin.chip555.org. (
                2017041000;   //num serie
                28800;        //refresco
                3600;         //reintentos
                604800;       //caducidad
                38400);       // tiempo en caché

        @ IN NS servidor01.chip555.org.
        servidor01.chip555.org. IN A 192.168.1.210
        WWW IN CNAME servidor01.chip555.org.
        ~~~


      `sudo nano /etc/bind/ri.192.168.1`  
      Con la siguiente configuracion:
        ~~~
        $TTL 38400

        @ IN SOA servidor01.sitioa.net. correoadmin.sitioa.net. (
          2017032100;   //num serie
          28800;        //refresco
          3600;         //reintentos
          604800;       //caducidad
          38400);       // tiempo en caché

        @ IN NS servidor01.
        210 IN PTR servidor01.gato.com.
        210 IN PTR servidor01.mosquito.com.
        210 IN PTR servidor01.escherichiacoli.es.
        210 IN PTR servidor01.chip555.org.

        ~~~
  
      `sudo service bind9 restart`  
      `sudo /etc/init.d/bind9 restart`
 
    `sudo apt-get install apache2`

   

      ~~~
      sudo mkdir -p /var/www/gato.com/html
      sudo mkdir -p /var/www/mosquito.com/html
      sudo mkdir -p /var/www/escherichiacoli.es/html
      sudo mkdir -p /var/www/chip555.org/html
      ~~~



   
        `sudo nano /var/www/gato.com/html/index.html`
          ~~~
          <html>
                  <head>
                          <title></title>
                  </head>
                  <body>
                          <img src="https://www.tn8.tv/media/cache/d9/df/d9df22561c4d5e43a550f2ff06591437.jpg"/>
                  </body>
          </html>
          ~~~
     
        `sudo nano /var/www/mosquito.com/html/index.html`
          ~~~
          <html>
                <head>
                        <title></title>
                </head>
                <body>
                        <img src="https://www.sciencenews.org/sites/default/files/2018/11/main/articles/112118_sm_mosquito_feat.jpg"/>
                </body>
          </html>
          ~~~
      
        `sudo nano /var/www/escherichiacoli.es/html/index.html`
          ~~~
          <html>
                  <head>
                          <title></title>
                  </head>
                  <body>
                          <img src="https://cdn.20m.es/img2/recortes/2017/08/21/527192-600-338.jpg?v=20170913165010"/>
                  </body>
          </html>
          ~~~
     
        `sudo nano /var/www/chip555.org/html/index.html`
          ~~~
          <html>
                  <head>
                          <title>Un chip555</title>
                  </head>
                  <body>
                          <img src="https://upload.wikimedia.org/wikipedia/commons/2/21/Signetics_NE555N.JPG"/>
                  </body>
          </html>
          ~~~

      ~~~
      sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/gato.com.conf
      sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/mosquito.com.conf
      sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/escherichiacoli.es.conf
      sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/chip555.org.conf
      ~~~

       `sudo nano /etc/apache2/sites-available/gato.com.conf`  
           ~~~
           <VirtualHost *:80>  
              ServerAdmin admin@gato.com
               ServerName gato.com
               ServerAlias www.gato.com
               DocumentRoot /var/www/gato.com/html
               ErrorLog ${APACHE_LOG_DIR}/error.log
               CustomLog ${APACHE_LOG_DIR}/access.log combined
           </VirtualHost>
           ~~~

       
       `sudo nano /etc/apache2/sites-available/mosquito.com.conf`  
           ~~~
           <VirtualHost *:80>
               ServerAdmin admin@mosquito.com
               ServerName mosquito.com
               ServerAlias www.mosquito.com
               DocumentRoot /var/www/mosquito.com/html
               ErrorLog ${APACHE_LOG_DIR}/error.log
               CustomLog ${APACHE_LOG_DIR}/access.log combined
           </VirtualHost>
           ~~~
       
       `sudo nano /etc/apache2/sites-available/escherichiacoli.es.conf`  
           ~~~
           <VirtualHost *:80>
               ServerAdmin admin@escherichiacoli.es
               ServerName escherichiacoli.es
               ServerAlias www.escherichiacoli.es
               DocumentRoot /var/www/escherichiacoli.es/html
               ErrorLog ${APACHE_LOG_DIR}/error.log
               CustomLog ${APACHE_LOG_DIR}/access.log combined
           </VirtualHost>
           ~~~
       `sudo nano /etc/apache2/sites-available/chip555.org.conf`  
           ~~~
           <VirtualHost *:80>
               ServerAdmin admin@chip555.org
               ServerName chip555.org
               ServerAlias www.chip555.org
               DocumentRoot /var/www/chip555.org/html
               ErrorLog ${APACHE_LOG_DIR}/error.log
               CustomLog ${APACHE_LOG_DIR}/access.log combined
           </VirtualHost>
           ~~~
    `sudo a2ensite gato.com.conf`  
    `sudo a2ensite mosquito.com.conf`  
    `sudo a2ensite escherichiacoli.es.conf`  
    `sudo a2ensite chip555.org.conf`

    `sudo a2dissite 000-default.conf`

    `sudo /etc/init.d/apache2 restart`  
    `sudo service apache2 restart`


      ~~~
      sudo htpasswd -c /var/www/sitioa.com/passwords user1
      sudo htpasswd -c /var/www/sitioa.com/passwords user2
      sudo htpasswd  /var/www/sitioa.com/passwords user3
      ~~~
  

   
    `sudo nano /etc/apache2/apache2.conf`  
        ~~~
          <Directory /var/www/escherichiacoli.es/html>
              AuthType Basic
              AuthName "ACCESO RESTRINGIDO."
              AuthUserFile /var/www/escherichiacoli.es/passwords
              Require user user01
              Options Indexes FollowSymLinks MultiViews
              AllowOverride  none
              Order Allow,deny
              allow from all
          </Directory>

          <Directory /var/www/chip555.org/html>
              AuthType Basic
              AuthName "ACCESO RESTRINGIDO."
              AuthUserFile /var/www/chip555.org/passwords
              Require valid-user
              Options Indexes FollowSymLinks MultiViews
              AllowOverride  none
              Order Allow,deny
              allow from all
          </Directory>
        ~~~
        

 
  `sudo /etc/init.d/apache2 restart`  
  `sudo service apache2 restart`

