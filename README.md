# Debian Setup

1.Descargar Debian 13 net install.

2.Inicie la instalación e ingrese la información.

3.Ingrese su usuario y password

4. Cree las particiones:

	4.1. Select Manual Installation and Select your HardDrive.
	
	4.2. EFI PARTITION-> 300MB -> Utilizar como EFI -> No Mounting Point
	
	4.3. Kernel Partition->2 GB-> EXT4 ->/BOOT
	
	4.4. Swap Partition-> 17GB(MEM RAM+1)->Utilizar como area de Intercambio.
	
	4.5. ROOT PARTITION->100 GB->BTRFS-> / ->Sistema de ficheros btrfs transaccional
	
	4.6. home PARTITION->EXT4/XFS->Todo el espacio y Punto de montaje /home

5. Selecciona Debian.org Repos.

6. Seleccionar SSH Server, y Utilidades Estandar del Sistema.(Texto)

7. Loguearse a tu nueva Terminal.

8. Loguearse como root.

9. Ejecutar el comando: df -Th para ver todas las particiones.

10. Montar el volumen BTRFS usando el comando: mount /dev/nvem01p4 /mnt

11. Moverse al /mnt y ejecutar la orden ls -l

12. Como resultado aparecera lo siguiente @rootfs

13. Moverse a cd @rootfs, esto entrara en el root folder, dentro del subvolumen.

14. Regresar y renombrar @rootfs a @: mv @rootfs/ @

15. Ejecutar: ls -l, donde antes decia @rootfs ahora dira @

16. Ejecutar nano /etc/fstab

17. En ese archivo buscar a donde se esta montando el subvolumen @rootfs, y modificar por @

18. Salvar el Archivo fstab

19. Editar el archivo /boot/grub/grub.cfg

20. Una linea tendra el @rootfs

21. Cerrar el Archivo.

22. Modificar la linea con: update-grub (iniciar sesion con su -)

23. El archivo de grub.cfg, deberia estar corregido.

24. Reiniciar con shutdown -r now

25. Ejecutar tasksel como root y elegir XFCE.

26. Re iniciar y el entorno grafico deberia mostrarse.

28. Instalar timeshift.

29. Crear Snapshot Clean.

30. Instalar todas las aplicaciones apt install sudo vim tmux screenfetch git htop nodejs npm mc default-jdk default-jre build-essential dkms linux-headers-$(uname -r) gdb wget curl sqlite3 mariadb-server newsboat gparted tlp tlp-rdw qbittorrent numix-icon-theme vim-gtk3 curl wget mugshot lightdm-gtk-greeter-settings bleachbit dosbox vlc flatpak innoextract thunderbird galculator catfish

31- Change Locales: sudo dpkg-reconfigure locales
Chrome:

1. sudo apt update && sudo apt install wget

2.wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb

3.sudo apt install ./google-chrome-stable_current_amd64.deb
