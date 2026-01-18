# PARTITIONS

Une partition de disque est une section d'un support de stockage, tel qu'un disque dur, un SSD ou une carte mémoire, qui est séparée pour permettre une gestion indépendante des données par le système d'exploitation.
 Cette opération, appelée partitionnement, consiste à diviser le disque en zones distinctes, chacune pouvant contenir un système de fichiers permettant d'organiser les informations stockées.
 Chaque partition peut être gérée séparément, ce qui est utile pour installer plusieurs systèmes d'exploitation, séparer les données personnelles des systèmes d'exploitation, ou améliorer la sécurité et l'organisation des fichiers.

 * Il existe des partitions:
 -primaires : systm d'exploitation
 -etendues : pr creer des partitions logiques en leur interieur
 -logiques : stocker des donnes mais pas de systm d'exploitation

# MOUNT POINT

Un mount point est un repertoire a partir duquel sont accessibles les donnees se trouvant sous forme d'un systeme de fichiers sur un epartition de disque dur ou un peripherique.

* Sous l'inux:

/ : première partition système du disque dur ;

/home : partition utilisateur du disque dur ;

/mnt/floppy : disquette (accès-type : /mnt/floppy/chemin/fichier).

# VOLUME CRYPTES

Les volumes chiffrés, également appelés volumes cryptés, sont des espaces de stockage protégés par un système de chiffrement qui permet de sécuriser les données contre tout accès non autorisé

A chaques demarrages de la VM une passphrase sera demande pour dechiffre le disque

# LVM

Dans une machine virtuelle, LVM peut être utilisé pour agrégater plusieurs disques virtuels ou partitions en un groupe de volumes (VG), à partir duquel des volumes logiques (LV) peuvent être créés, formatés avec un système de fichiers (FS) et montés comme des partitions ordinaires.

Cette approche facilite des opérations comme l'extension dynamique de volumes, le déplacement de données entre supports physiques en temps réel, ou encore la création de snapshots pour des sauvegardes instantanées


# Passwords:
- passphrase: ```lechocolatmedonneleschocottes```
- user: ```lheteau``` / psw: ```1234Choco.```
- user: ```root``` / psw: ```1234Choco.```

`chage -d 0 <user>` force a arriver un user a son day 0 

`chage -l <user>` donne info statu mdp

`sudo passwd <user>` changer le mdp d'un user


# Commandes

`lsblk` pour afficher partition

`su -` pour basculer vers un autre utilisateur (su -root pour se co en superutilisateur avec un environnement complet)

`apt update` pour mettre a jour le systeme

`apt install sudo` pour installer le package sudo

`adduser lheteau sudo` rajouter l'user lheteau au groupe sudo

// `sudo delluser `

// `sudo adduser` creer un user avec toutes les infos demadees!

// `getent passwd <user>` pr voir les details du grp password et donc si le user existe

`getent group sudo` donne les infos du groupe sudo(nom : emplacement du mdp (x=ect/gshadow) : id : liste des users)


`reboot` redemarrer

`sudo -V` affiche la version de sudo ect


## configuring sudo

`sudo visudo` est un outil sécurisé utilisé pour modifier le fichier /etc/sudoers, qui contient les règles d'accès aux privilèges pour la commande sudo.

`sudo mkdir -p /var/..` cree un dossier et tout ses fichiers parents necessaires dans un endroit specifique, meme si il existe encore pas

`sudo touch /var/../sudo.log` creer fichier sudo.log

* installation et config ssh

`sudo apt install openssh-server -y` installer ssh

`sudo nano /etc/ssh/sshd_config` acceder au fichier sshd_config (changer port a 4242 + mettre permitrootlogin a no)PEUT PAS SE CO EN ROOT SUR TERM EXTERN

`sudo nano /etc/ssh/ssh_config` pr changer port a 4242

`sudo service ssh restart` update le service ssh

`sudo service ssh status` verifier les ports mis a jour
## `ssh <user>@localhost -p 4142` pour se connecter a la machine virtuelle depuis son ordi

## UFW 

`sudo apt install ufw` installer ufw

`sudo ufw enable` activer parfeu

`sudo ufw allow 4242` autoriser son parefeu a accepter les connections sur le port 4242

`sudo ufw status` check status de notre parefeu

## sudo policies

`touch /etc/sudoers.d/sudo_config` store la police dedans (`nano` pe edite)

`mkdir /var/log/sudo` pr stocker chaques commandes

`nano /etc/sudoers.d/sudo_config` :
	
	`passwd_tries=3` :Total tries for entering the sudo password.
	
	`badpass_message="message"`: The message that will show when the password failed.
	
	`logfile="/var/log/sudo/sudo_config"`: Path where will the sudo logs will be stored.
	
	`log_input, log_output`: What will be logged.
	
	`iolog_dir="/var/log/sudo"`: What will be logged.
	
	`requiretty`: TTY become required
	
	`secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin"`: Folders that will be excluded of sudo

## password policy

`nano /etc/login.defs` le fichier dans lequel il y a les regles qd au motdepasse
	
	`PASS_MAX_DAYS`: Maximum number of days before password expires.
	
	`PASS_MIN_DAYS`: Minimum number of days before password can be changed.
	
	`PASS_WARN_AGE`: Number of days before password expiration to show warning.

`sudo apt install libpam-pwquality` librairie pr les mdp

`nano /etc/pam.d/common-password` edit PAM configuration (Pluggable Authentication Modules)
	
	minlen=10 ➤ The minimum characters a password must contasudo in.
	
	ucredit=-1 ➤ The password must contain at least one capital letter. We must write it with a - sign, as this is how it 
	
	knows that it refers to minimum characters; if we put a + sign it will refer to maximum characters.
	
	dcredit=-1 ➤ The password must contain at least one digit.
	
	lcredit=-1 ➤ The password must contain at least one lowercase letter.
	
	maxrepeat=3 ➤ The password cannot have the same character repeated three consecutive times.
	
	reject_username ➤ The password cannot contain the username within itself.
	
	difok=7 ➤ The password must contain at least seven different characters from the last password used.
	
	enforce_for_root ➤ We will implement this password policy for root.

# MOT DE PASSE	root: 1234Choco.
# MOT DE PASSE	lheteau: 1234Choco.

# script
```

```


## crontab

`sudo crontab -u root -e` edit le crontab (lancer tt les 10mins)

## RULES PORT (UFW)

`sudo ufw status numbered` avoir le statut des port 

`sudo ufw delete <num>` supprimer la regle concernant le port numero...

`sudo ufw allow <port>` rajouter la regle avec le port...



