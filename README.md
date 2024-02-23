# Ubuntu-Bspwm
> Esto es una configuracion sobre bspwm en ubuntu 23.10 en la cual conlleva una customización sobre la terminal, polybar, picom y mas complementos.
 ## Paquetes Principales:
 + bspwm **(al descargar bspwm se descarga automaticamente sxhkd)**
 + polybar
 + suckless-tools **(esto es para el menu de selección de escritorios)**

 ## Paquetes Secundarios:
 + neofetch
 + git
 + nitrogen
 + lxappearance
 + kitty
 + picom
 + ranger
 + htop
 + zsh

### Pasos antes de cambiar a bspwm:

#### En ubuntu hay que crear 3 directorios de configuracion para poder usarlo correctamente.

`mkdir ~/.config/bspwm`

`mkdir ~/.config/sxhkd`

`mkdir ~/.config/polybar`

#### Luego hay que copiar las configuraciones preterminadas de cada uno.

`cp /usr/share/doc/bspwm/examples/bspwmrc ~/.config/bspwm/`

`cp /usr/share/doc/bspwm/examples/sxhkdrc ~/.config/sxhkd/`

`cp /usr/share/doc/polybar/examples/config.ini ~/.config/polybar/`

#### El siguiente paso es crear un ejecutable en la polybar para que se ejecute.

`$HOME/.config/polybar/launch.sh`

#### Configuracion del launch.sh:
```
#!/usr/bin/env bash

# Terminate already running bar instances
# If all your bars have ipc enabled, you can use 
polybar-msg cmd quit
# Otherwise you can use the nuclear option:
# killall -q polybar

# Launch bar1 and bar2
echo "---" | tee -a /tmp/polybar1.log /tmp/polybar2.log
polybar example 2>&1 | tee -a /tmp/polybar1.log & disown

echo "Bars launched..."
```





   
 
