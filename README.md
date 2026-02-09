# Debian Setup

1.Descargar Debian 13 net install o standard.

2.Inicie la instalación e ingrese la información.

3.Ingrese su usuario y password

4. Cree las particiones:

	4.1. Select Manual Installation and Select your HardDrive.
	
	4.2. EFI PARTITION----->300 MB--> EFI---->N/A
	
	4.3. KERNEL PARTITION-->2 GB----> EXT4--->/BOOT
	
	4.4. SWAP PARTITION---->17GB(MEM RAM+1)-->N/A
	
	4.5. ROOT PARTITION---->90 GB--->BTRFS->/
	
	4.6. HOME PARTITION---->ALL----->EXT4/XFS->/HOME

5. Finalizar la instalación.

## Configurando BTRFS para poder usar Timeshift

1. Ejecutar el comando:
  
  		df -Th
   
2. Montar el volumen BTRFS usando el comando:

   		sudo mount /dev/nvem01p4 /mnt

3. Moverse al /mnt y ejecutar la orden ls -l

4. Como resultado aparecera lo siguiente @rootfs

5. Moverse a cd @rootfs, esto entrara en el root folder, dentro del subvolumen.

6. Regresar y renombrar ****@rootfs** a @: 

       sudo mv @rootfs/ @

7. Ejecutar: ls -l, donde antes decia **@rootfs ahora dira @**

8. Ejecutar:

    	sudo nano /etc/fstab

9. En ese archivo buscar a donde se esta montando el subvolumen **@rootfs, y modificar por @**

10. Salvar el Archivo fstab

11. Actualizar Grub:

    	sudo update-grub

12. Reiniciar con :

      sudo shutdown -r now


## Instalar Xfce4 Basico

    	sudo apt install synaptic timeshift tlp btrfs-progs gparted gsmartcontrol bleachbit xfce4 lightdm htop wget curl network-manager-gnome network-manager arandr acpi screenfetch mc tmux emacs vim vim-gtk3 git

## Instalacion final con Xfce4-goodies y todas las herramientas

	sudo apt install default-jdk default-jre python3-pip nodejs gdb build-essentialmflatpak mugshot catfish lightdm-gtk-greeter-settings bluez blueman pulseaudio-module-bluetooth bluez-tools elementary-xfce-icon-theme breeze-cursor-theme menulibre conky-all sqlite3 sqlitebrowser geany galculator xfce4-goodies p7zip-full greybird-gtk-theme crawl-tiles aisleriot skladnik xye wesnoth dosbox cowsay gnome-mines evince qbittorrent vlc innoextract 
	
## Crear Snapshot "Clean Install" ejecutando:

    sudo timeshift --btrfs

    sudo timeshift --create --comments "Clean install"


## Otros comandos útiles

### Reconfigurar locales:

	sudo dpkg-reconfigure locales

### Añadir repos para instalar Chrome:

	sudo extrepo enable google_chrome

### Add this line to lightdm.conf to remember the last user:

	[Seat:*]
	greeter-hide-users=false

### Add this line to lightdm-gtk-greeter.conf

	hide-user-image = true

	indicators = ~host;~spacer;~clock;~spacer;~session;~layout;~a11y;~power

### Instalar Flatpack

Instalar:

	  sudo apt update && sudo apt install flatpak

Añade Repositorios:

  	flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo

### Add, Delete Users
Añade un usuario:

	sudo adduser adolfo

Borra un usuario:

	sudo deluser adolfo

Boora un usuario y el folder home:

	sudo deluser --remove-home adolfo

Añade el usuario a sudoers:

	sudo usermod -aG sudo adolfo

### Habilitar Actualizaciones Automáticas

Actualiza e instala los paquetes necesarios:

	sudo apt update && sudo apt install unattended-upgrades

Llamar el asistente de Configuración:

	sudo dpkg-reconfigure --priority=low unattended-upgrades

Revisa la configuarción

	sudo nano /etc/apt/apt.conf.d/20auto-upgrades

Debe Contener lo siguiente:

	APT::Periodic::Update-Package-Lists "1";
	APT::Periodic::Unattended-Upgrade "1";


### Instalar Wine

	https://gitlab.winehq.org/wine/wine/-/wikis/Debian-Ubuntu

### Configuracion de XFCE4 

	/home/adolfo/.local/share/xfce4/terminal/colorschemes/

	




