# Préparation

Sur Debian Stretch Mate

Ajoutez l’utilisateur “odr” et donnez lui un mot de passe

    $ su
    $ adduser odr

Puis modifiez les droits de “odr”

    $ visudo -f /etc/sudoers

Ajoutez la ligne suivante après “root All=(ALL:ALL) ALL”

    odr ALL=(ALL:ALL) ALL

Et rebootez votre PC :

    $ reboot

# Installation d'ODR

    $ su odr
    $ cd
    $ sudo apt-get install git
    $ git clone https://github.com/LyonelB/ODR-Mux.git
    $ mv /home/odr/ODR-Mux/install.sh /home/odr
    $ chmod +x install.sh
    $ ./install.sh

## Mux La Roche-sur-Yon local

### Installation de Supervisor
    
    $ sudo apt-get install supervisor
    $ mv /home/odr/ODR-Mux/MUX-LRSY/config /home/odr

### Configuration de Supervisor

    $ sudo ln -s /home/odr/config/supervisor/enc-JET.conf /etc/supervisor/conf.d/enc-JET.conf
    $ sudo ln -s /home/odr/config/supervisor/enc-GRAFFITI.conf /etc/supervisor/conf.d/enc-GRAFFITI.conf
    $ sudo ln -s /home/odr/config/supervisor/enc-SUN.conf /etc/supervisor/conf.d/enc-SUN.conf
    $ sudo ln -s /home/odr/config/supervisor/enc-EURADIO.conf /etc/supervisor/conf.d/enc-EURADIO.conf
    $ sudo ln -s /home/odr/config/supervisor/enc-RCA.conf /etc/supervisor/conf.d/enc-RCA.conf
    $ sudo ln -s /home/odr/config/supervisor/enc-BONHEUR.conf /etc/supervisor/conf.d/enc-BONHEUR.conf
    $ sudo ln -s /home/odr/config/supervisor/enc-OCEANE.conf /etc/supervisor/conf.d/enc-OCEANE.conf
    $ sudo ln -s /home/odr/config/supervisor/enc-FORUM.conf /etc/supervisor/conf.d/enc-FORUM.conf
    $ sudo ln -s /home/odr/config/supervisor/enc-MARIA.conf /etc/supervisor/conf.d/enc-MARIA.conf
    $ sudo ln -s /home/odr/config/supervisor/enc-ORIENT.conf /etc/supervisor/conf.d/enc-ORIENT.conf
    $ sudo ln -s /home/odr/config/supervisor/enc-MELODY.conf /etc/supervisor/conf.d/enc-MELODY.conf
    $ sudo ln -s /home/odr/config/supervisor/enc-CAPSAO.conf /etc/supervisor/conf.d/enc-CAPSAO.conf
    $ sudo ln -s /home/odr/config/supervisor/enc-PITCHOUN.conf /etc/supervisor/conf.d/enc-PITCHOUN.conf
    $ sudo ln -s /home/odr/config/supervisor/mux.conf /etc/supervisor/conf.d/mux.conf
    $ sudo ln -s /home/odr/config/supervisor/mod.conf /etc/supervisor/conf.d/mod.conf
    
## Mux Nantes local

### Installation de Supervisor
    
    $ sudo apt-get install supervisor
    $ sudo mv /home/odr/ODR-Mux/MUX-Nantes/config /home/odr
    
### Configuration de Supervisor

    $ sudo ln -s /home/odr/config/supervisor/enc-radio1.conf /etc/supervisor/conf.d/enc-radio1.conf
    $ sudo ln -s /home/odr/config/supervisor/enc-radio2.conf /etc/supervisor/conf.d/enc-radio2.conf
    $ sudo ln -s /home/odr/config/supervisor/enc-radio3.conf /etc/supervisor/conf.d/enc-radio3.conf
    $ sudo ln -s /home/odr/config/supervisor/enc-radio4.conf /etc/supervisor/conf.d/enc-radio4.conf
    $ sudo ln -s /home/odr/config/supervisor/enc-radio5.conf /etc/supervisor/conf.d/enc-radio5.conf
    $ sudo ln -s /home/odr/config/supervisor/enc-radio6.conf /etc/supervisor/conf.d/enc-radio6.conf
    $ sudo ln -s /home/odr/config/supervisor/enc-radio7.conf /etc/supervisor/conf.d/enc-radio7.conf
    $ sudo ln -s /home/odr/config/supervisor/enc-radio8.conf /etc/supervisor/conf.d/enc-radio8.conf
    $ sudo ln -s /home/odr/config/supervisor/enc-radio9.conf /etc/supervisor/conf.d/enc-radio9.conf
    $ sudo ln -s /home/odr/config/supervisor/enc-radio10.conf /etc/supervisor/conf.d/enc-radio10.conf
    $ sudo ln -s /home/odr/config/supervisor/enc-radio11.conf /etc/supervisor/conf.d/enc-radio11.conf
    $ sudo ln -s /home/odr/config/supervisor/enc-radio12.conf /etc/supervisor/conf.d/enc-radio12.conf
    $ sudo ln -s /home/odr/config/supervisor/enc-radio13.conf /etc/supervisor/conf.d/enc-radio13.conf
    $ sudo ln -s /home/odr/config/supervisor/mux.conf /etc/supervisor/conf.d/mux.conf
    $ sudo ln -s /home/odr/config/supervisor/mod.conf /etc/supervisor/conf.d/mod.conf
    
## Commun aux deux Mux

    $ sudo nano /etc/supervisor/supervisord.conf

et ajoutez les lignes suivantes :

    [inet_http_server]
    port = 9100
    username = user ; Auth username
    password = pass ; Auth password

Pour que les fichiers de configuration soient pris en compte par supervisor :

    $ sudo supervisorctl reread
    $ sudo supervisorctl update
    $ sudo reboot
