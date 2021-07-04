# Auto-arranque-SC-RPi
Inicio automatico de SuperCollider en Raspberry Pi OS, basado en el archivo de compilación d SuperCollider en Raspberry Pi.

## Crea un script bash
Lo que hace este archivo es indicar en el arranque que busque la ruta donde esta instalado supercollider, se espera 10 segundos y corre el archivo e código llamado micodigo.scd. 
```
#!/bin/bash
export PATH=/usr/locl/bin:$PATH
export DISPLAY=:0.0
sleep 10
sclang micodigo.scd
```
## Cambia el modo
Abre la terminal y cambia el modo del script anterior
```
chmod +x ~/autostart.sh
```
## Colocalo en el arranque
```
```
## Crea un código en SuperCollider
```
```
