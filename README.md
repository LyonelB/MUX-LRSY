# Installation

Sur Debian Stretch

Ajoutez l’utilisateur “odr” et donner lui un mot de passe

    $ su
    $ adduser odr

Puis modifiez les droits de “odr”

    $ visudo -f /etc/sudoers

Ajoutez la ligne suivante après “root All=(ALL:ALL) ALL”

odr ALL=(ALL:ALL) ALL

Et rebootez votre PC :

    $ reboot

Installation d'ODR

    $ su odr
    $ cd
    $ sudo apt-get install git
    $ git clone https://github.com/LyonelB/ODR-Mux.git
    $ cd ODR-Mux
    $ chmod +x install.sh
    $ ./install.sh


## Mux La Roche-sur-Yon local

## Mux Nantes local
