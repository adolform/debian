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

5. Finalizar la instalación.


## Configurando BTRFS para poder usar Timeshift

1. Ejecutar el comando: df -Th para ver todas las particiones.

2. Montar el volumen BTRFS usando el comando: mount /dev/nvem01p4 /mnt

3. Moverse al /mnt y ejecutar la orden ls -l

4. Como resultado aparecera lo siguiente @rootfs

5. Moverse a cd @rootfs, esto entrara en el root folder, dentro del subvolumen.

6. Regresar y renombrar @rootfs a @: mv @rootfs/ @

7. Ejecutar: ls -l, donde antes decia @rootfs ahora dira @

8. Ejecutar nano /etc/fstab

9. En ese archivo buscar a donde se esta montando el subvolumen @rootfs, y modificar por @

10. Salvar el Archivo fstab

11. Modificar la linea con: sudo update-grub-

12. El archivo de grub.cfg, deberia estar corregido.

13. Reiniciar con shutdown -r now

14. Instalar Terminal Tools y un entorno de Escritorio Básico.

    sudo apt install timeshift i3 wget tlp btrfs-progs mc tmux lightdm htop newsboat vim git

### Crear Snapshot "Clean Install" ejecutando:

    sudo timeshift --btrfs

    sudo timeshift --create --comments "Clean install with I3 only"

## Otros comandos útiles

### Reconfigurar locales:

	sudo dpkg-reconfigure locales

### Añadir repos para instalar Chrome y Brave

	sudo extrepo enable brave_release
	sudo extrepo enable google-chrome



