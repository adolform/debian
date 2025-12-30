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

16. Instalar Terminal Tools y un entorno de Escritorio Básico.

    	sudo apt install timeshift tlp btrfs-progs gparted gsmartcontrol bleachbit

### Crear Snapshot "Clean Install" ejecutando:

    sudo timeshift --btrfs

    sudo timeshift --create --comments "Clean install"

## Otros comandos útiles

### Reconfigurar locales:

	sudo dpkg-reconfigure locales

### Añadir repos para instalar Chrome y Brave:

	sudo extrepo enable google_chrome

	sudo extrepo enable brave_release

### Instalacion final con Xfce4 y Herramientas Gráficas

	sudo apt install mc newsboat fastfetch tmux htop cowsay qbittorrent vlc putty innoextract dosbox default-jdk default-jre python3-pip nodejs gdb build-essential emacs vim vim-gtk3 git wget flatpak

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
### Eliminar rastros de libreoffice y firefox

Para Firefox

	rm -rf ~/.mozilla
	
	rm -rf ~/.cache/mozilla

Para LibreOffice

	rm -rf ~/.config/libreoffice

### Instalar Wine

1. Habilitar Multi-arquitectura (32 bits):
   
    sudo dpkg --add-architecture i386 y luego sudo apt update.

2. Agregar el Repositorio de WineHQ:

	sudo mkdir -p /etc/apt/keyrings y wget -O /etc/apt/keyrings/winehq-archive.key dl.winehq.org.


	sudo wget -NP /etc/apt/sources.list.d/ dl.winehq.org
	
	sudo apt update

 	sudo apt install --install-recommends winehq-stable.


Ejecuta winecfg para la primera inicialización. Esto creará el directorio ~/.wine y te pedirá instalar componentes adicionales como mono y gecko.
Verificar la Instalación:
Ejecuta wine --version para confirmar la versión instalada. 

	




