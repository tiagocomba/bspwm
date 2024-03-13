# Ubuntu-Bspwm
> Esto es una configuración sobre bspwm en ubuntu 23.10 en la cual conlleva una customización sobre la terminal, polybar, picom y mas complementos.
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
 + curl

### Pasos antes de cambiar a bspwm:

#### En ubuntu hay que crear 3 directorios de configuración para poder usarlo correctamente.

`mkdir ~/.config/bspwm`

`mkdir ~/.config/sxhkd`

`mkdir ~/.config/polybar`

#### Luego hay que copiar las configuraciones preterminadas de cada uno.

`cp /usr/share/doc/bspwm/examples/bspwmrc ~/.config/bspwm/`

`cp /usr/share/doc/bspwm/examples/sxhkdrc ~/.config/sxhkd/`

`cp /usr/share/doc/polybar/examples/config.ini ~/.config/polybar/`

#### El siguiente paso es crear un ejecutable en la polybar para que se ejecute.

`$HOME/.config/polybar/launch.sh`

#### Configuración del launch.sh:
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
#### Ahora hay que otorgale permisos al ejecutable.

`chmod +x $HOME/.config/polybar/launch.sh`

#### El Siguiente paso es: Crear el directorio de config de Picom y Kitty.

`mkdir  ~/.config/picom`

`nano  ~/.config/picom/picom.conf`

`nano  ~/.config/kitty/kitty.conf`

`nano  ~/.config/kitty/color.ini`

### Ahora Descargar oh-my-zsh y powerlevel10k.

`sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"`

`git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k`





   
 
