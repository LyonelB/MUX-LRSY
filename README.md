# Préparation

Sur Debian Stretch Mate

Ajoutez l’utilisateur “odr” et donner lui un mot de passe

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
    $ sudo mv /home/odr/ODR-Mux/install.sh /home/odr
    $ chmod +x install.sh
    $ ./install.sh

## Mux La Roche-sur-Yon local

### Installation de Supervisor
    
    $ sudo apt-get install supervisor
    $ sudo mv /home/odr/ODR-Mux/MUX-LRSY/config /home/odr

## Mux Nantes local

### Installation de Supervisor
    
    $ sudo apt-get install supervisor
    $ sudo mv /home/odr/ODR-Mux/MUX-Nantes/config /home/odr
    
## Commun aux deux Mux

Ajoutez des "liens" à supervisor :

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
