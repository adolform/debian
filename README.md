# Debian Setup

1.Descargar Debian 13 net install.

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
   
4. Montar el volumen BTRFS usando el comando:

   sudo mount /dev/nvem01p4 /mnt

6. Moverse al /mnt y ejecutar la orden ls -l

7. Como resultado aparecera lo siguiente @rootfs

8. Moverse a cd @rootfs, esto entrara en el root folder, dentro del subvolumen.

9. Regresar y renombrar ****@rootfs** a @: mv @rootfs/ @**

10. Ejecutar: ls -l, donde antes decia **@rootfs ahora dira @**

11. Ejecutar nano /etc/fstab

12. En ese archivo buscar a donde se esta montando el subvolumen **@rootfs, y modificar por @**

13. Salvar el Archivo fstab

14. Modificar la linea con: sudo update-grub-

15. El archivo de grub.cfg, deberia estar corregido.

16. Reiniciar con shutdown -r now

17. Instalar Terminal Tools y un entorno de Escritorio Básico.

    sudo apt install timeshift wget tlp btrfs-progs mc tmux lightdm htop vim git wget newsboat xfce4

### Crear Snapshot "Clean Install" ejecutando:

    sudo timeshift --btrfs

    sudo timeshift --create --comments "Clean install with I3 only"

## Otros comandos útiles

### Reconfigurar locales:

	sudo dpkg-reconfigure locales

### Añadir repos para instalar Chrome y Brave

	sudo extrepo enable brave_release
	sudo extrepo enable google-chrome

### Instalacion final con Xfce4 y Herramientas Gráficas

	sudo apt install xfce4-goodies mugshot catfish vlc 7zip google-chrome-stable brave-browser putty emacs sqlite3 vim gtk3 default-jdk default-jre nodejs gdb audacious *icon-theme

### Add, Delete Users
Añade un usuario:
sudo adduser leah

Borra un usuario:
sudo deluser leah

Boora un usuario y el folder home:
sudo deluser --remove-home leah 

Añade el usuario a sudoers:
sudo usermod -aG sudo leah


