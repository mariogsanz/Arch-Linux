# Arch-Linux VM
## Descarga la ISO de ArchLinux
https://archlinux.org/download/

## Crea una nueva máquina virtual
* Selecciona la ISO de ArchLinux
* Selecciona Debian como tipo de SO
* Selecciona UEFI como tipo de firmware (con BIOS la configuración cambia ligeramente)
* Configura la máquina virtual

## Iniciamos la máquina virtual
* Selecciona el modo de instalación

## Configuramos Arch Linux
* Cambiamos el idioma del teclado

```shell
loadkeys es
```

* Comprobamos que tenemos conexión

```shell
ip link
```
La interfaz tiene que estar `UP`

```shell
ip a
```
Comprobamos que tenemos una dirección asignada

```shell
ping -c 1 archlinux.org
```
Comprobamos que podemos hacer `ping`
