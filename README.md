# Auto-arranque-SC-RPi
Inicio automático de SuperCollider en Raspberry Pi OS, basado en el archivo de compilación de SuperCollider para Raspberry Pi. Probado en Raspberry Pi 4 con Raspberry OS Desktop.

## Crea un script bash
Lo que hace este archivo es indicar en el arranque que busque la ruta donde está instalado SuperCollider, se espera 10 segundos y corre el archivo de código llamado micodigo.scd. 
```
#!/bin/bash
export PATH=/usr/locl/bin:$PATH
export DISPLAY=:0.0
sleep 10
sclang micodigo.scd
```
## Cambia el modo
Abre la terminal y cambia el modo del script anterior.
```
chmod +x ~/autostart.sh
```
## Colocalo en el arranque
En una terminal abre crontab.
```
crontab -e
```
Al final del documento que se abre escribe la siguiente línea.
```
@reboot cd /home/pi && ./autostart.sh
```
## Crea un código en SuperCollider
En el script de SuperCollider llamado micodigo.scd puedes poner este código, que hará sonar un batimento al iniciar la Raspberry Pi.
```
s.waitForBoot{{SineOsc.ar([400, 440], 0, 0.5)}.play}
```
## Haz un reboot de la Raspberrypi
```
sudo reboot
```
El sonido comienza si todo salío bien.

Para parar el sonido escribe en la terminal la siguiente línea:
```
killall jackd sclang scsynth
```
Esto se supone que corre en una RPi con monitor HDMI conectado. Si quieres iniciar una RPi 4 sin el monitor escribe la siguiente línea en el /boot/config.txt. En una terminal tecela:
```
sudo nano /boot/config.txt
```
Descomenta la línea que dice #hdmi_force_hotplug=1

