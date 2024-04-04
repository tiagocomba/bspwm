# Ubuntu-Bspwm
> Esto es una configuración sobre bspwm en ubuntu 23.10 en la cual conlleva una customización sobre la terminal, polybar, picom y mas complementos.
 ## Paquetes Principales:
 + bspwm **(al descargar bspwm se descarga automaticamente sxhkd)**
 + polybar
 + suckless-tools **(esto es para el menu de selección de escritorios)**

 ## Paquetes Secundarios:
 + neofetch
 + lolcat
 + git
 + nitrogen
 + feh
 + lxappearance
 + kitty
 + thunar
 + picom
 + ranger
 + htop
 + btop
 + cava
 + cmatrix
 + tty-clock
 + pipes.sh or pipes-sh
 + zsh
 + neovim
 + ninja
 + lsd
 + bat
 + curl
 + make
 + pamixer
 + pavucontrol
 + playerctl
 + dunst
 + flameshot
 + xsecurelock

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

### Descargar los Plugins de zsh:

`sudo apt install  zsh-syntax-highlighting`

`sudo apt install  zsh-autosuggestions`

`echo "source /usr/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh" >> /home/tiago-comba/.zshrc`

 `echo "source /usr/share/zsh-autosuggestions/zsh-autosuggestions.zsh" >> /home/tiago-comba/.zshrc`

### Descargas de Fuentes:

`https://github.com/microsoft/cascadia-code.git`

`sudo cp -r /home/tu-usuario/carpeta-donde-este-situada-la-fuente/cascadia-code /usr/share/fonts/opentype`

### Personalizar Nano:

`git clone https://github.com/valerie-makes/nano-highlight.git`

Dentro de la carpeta donde lo hayamos descargado, entrar a nano-highlight y ejecutar este comando:

`make install`

`echo "include ~/.nano/syntax/ALL.nanorc >> ~/.nanorc"`

### Personalizar Neofetch:

Ir al perfil de: `https://github.com/Chick2D/neofetch-themes`

Copiar la config que mas te guste y pegarla en:

`.config/neofetch/config.conf`

### Personalizar Resolucion de pantalla:

Crear un archivo en esta ruta, si existe solo editarlo:

`sudo nano /etc/X11/xorg.conf`

copiar segun tus preferencias:

`Section "Monitor"
    Identifier "Monitor0"
    Option "PreferredMode" "1920x1080"
    Option "RefreshRate" "75"
EndSection`

### Opcional Fork de Picom animaciones:

Descargar las dependencias:

`libxext-dev libxcb1-dev libxcb-damage0-dev libxcb-xfixes0-dev libxcb-shape0-dev libxcb-render-util0-dev libxcb-render0-dev libxcb-randr0-dev libxcb-composite0-dev libxcb-image0-dev libxcb-present-dev libxcb-xinerama0-dev libxcb-glx0-dev libpixman-1-dev libdbus-1-dev libconfig-dev libgl1-mesa-dev libpcre2-dev libpcre3-dev libevdev-dev uthash-dev libev-dev libx11-xcb-dev`

Descargar ninja si aun no lo descargaste:

`sudo apt install ninja-build`

Luego clonar este repositorio:

`git clone https://github.com/jonaburg/picom.git`

Acceder a su carpeta:

`cd picom`

Build:

`meson --buildtype=release . build`

`ninja -C build`

`sudo ninja -C build install`

Reiniciar Picom:

`killall picom`

`picom &`

### Neomutt (gestor de correo en terminal):

clonar primero este repositorio:

`git clone https://github.com/neomutt/neomutt.git`

Luego ir a la carpeta creada:

`cd neomutt`

Ejecutar estos comandos:

`./configure`

si te sale algun error descargar las dependencias restantes.

`make`

`make install`

### Themes Rofi:

Clonar este repositorio:

`git clone https://github.com/Murzchnvok/rofi-collection.git`

Entrar al directorio:

`cd rofi-collection`

Copiar la config que te guste:

`sudo cp -r nord/nord.rasi /usr/share/rofi/themes/`

Tambien puede estar los temas de rofi en esta carpeta:

`sudo cp -r nord/nord.rasi $HOME/.local/share/rofi/themes/`

Si no queres copiar cada uno de las config ejecuta este comando:

`sudo find ~/rofi-collection -name "*.rasi" -exec cp {} /usr/share/rofi/themes/ \;`

Luego en la terminal ejecutar este comando y elegir el tema:

`rofi-theme-selector`

### Descargar Neovim y LazyVim

Clonear el repositorio de Neovim:

`git clone https://github.com/neovim/neovim.git`

Instalar neovim:

```
cd neovim
make CMAKE_BUILD_TYPE=Release
sudo make install
```

Resetear la carpeta de config:

`rm -rf  ~/.config/nvim`

Opcional:

`rm -rf  ~/.local/share/nvim`

`rm -rf  ~/.local/state/nvim`

`rm -rf  ~/.cache/nvim`

Clonar LazyVim:

`git clone https://github.com/LazyVim/starter ~/.config/nvim`

Luego entrar a nvim y se descargara LazyVim y listo.















   
 
