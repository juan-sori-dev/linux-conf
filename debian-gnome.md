# Configurar Debian

---

## Atajos Personalizados

- Configurar atajo `Ctrl` + `Shift` + `T` para la terminal `gnome-terminal`.

## Usuario como root

- En la terminal `$ su`, y pongo la contraseña de root
  - (si no la se, la establezco con el comando ` $ sudo passwd root`)
- En la terminal `# nano /etc/sudoers`
- Buscar y añadir `Defaults env_reset,pwfeedback`
- Debajo de `root ALL=(ALL:ALL) ALL`
- Añadir `<usuario> ALL=(ALL:ALL) ALL`

## Modificar el Grub

- En la terminal `$ sudo nano /etc/default/grub`
- Cambio `GRUB_TIMEOUT` a `0`
- Añado `quiet splash` para mostrar plymouth
- Descomento `GRUB_GFXMODE` y lo igualo a la resolución de la pantalla, ej: `1920x1080`
- Guardo los cambios y al salir del archivo actualizo el grub `$ sudo uptade-grub`

## Quitar programas que no uso

- Desinstalo todo lo que no quiera usar, con synaptic y genome-software
- En la terminal `$ sudo apt autoremove`

## Añadir repositorios extra

- En la aplicación Software Updates marco todos los repos de la pestaña Debian Software
- Si quiero puedo añadir los repos de los backports `deb http://deb.debian.org/debian bookworm-backports main`
- En la terminal `$ sudo apt update && sudo apt upgrade -y` para que actualize los repos y todo el softare

## Instalar utilidades

- Gdebi para gestionar la instalación de archivos .deb `$ sudo apt install gdebi gdebi-core synaptic`
- Utiles para diferentes formatos de disco `$ sudo apt install exfat-fuse hfsplus hfsutils ntfs-3g`
- Compresores y descompresores `$ sudo apt install p7zip-full p7zip-rar rar unrar`
- Codecs extra `$ sudo apt install ffmpeg libavcodec-extra gstreamer1.0-libav gstreamer1.0-plugins-ugly gstreamer1.0-plugins-bad gstreamer1.0-pulseaudio vorbis-tools`
- Fuentes extra `$ sudo apt-get install fonts-freefont-ttf fonts-freefont-otf fonts-ubuntu`
- Fuentes de Microsoft `$ sudo apt-get install ttf-mscorefonts-installer`

## Instalar Flatpak

- Poner todo uno por uno en la terminal

```bash
$ sudo apt install flatpak
$ sudo apt install gnome-software-plugin-flatpak
$ sudo flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```

- Luego hay que reiniciar el sistema

## Instalar Waydroid

- Instalar prerrequisitos `$ sudo apt install curl ca-certificates -y`
- Añadir repositorio oficial `curl -s https://repo.waydro.id | sudo bash`
  - Si el comando no detecta la distro automáticamente, se puede aladir una anexando -s < DISTRO >. Las soportadas acutalmente son: **mantic, focal, jammy, kinetic, lunar, noble, plucky, questing, bookworm, bullseye, trixie, sid**
- Instalar Waydroid `$ sudo apt install waydroid -y`
- Google Play Certification:
  - En la terminal `$ sudo waydroid shell`
  - Dentro escribir `ANDROID_RUNTIME_ROOT=/apex/com.android.runtime ANDROID_DATA=/data ANDROID_TZDATA_ROOT=/apex/com.android.tzdata ANDROID_I18N_ROOT=/apex/com.android.i18n sqlite3 /data/data/com.google.android.gsf/databases/gservices.db "select * from main where name = \"android_id\";"`
  - Usar la cadena de numeros para certificar el dispositivo en: https://docs.waydro.id/faq/google-play-certification
  - Esperar un poco y reiniciar el android

## Instalar software general que utilizo

- En la terminal `$ sudo apt instal vlc zeal`
- Descargar vscode:

## Personalizar Gnome

- https://youtu.be/osz8TmKLey0?si=8w-_LAHJE5vV-faK
- https://youtu.be/oPf_0h8mG2Q?si=qM16PQQD9WnkoUdg
