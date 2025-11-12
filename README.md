# 🧠 Instalación de mi entorno Zsh personalizado (Ubuntu)

Configuración modular con **Zsh**, **Oh My Zsh**, **Oh My Posh**, y utilidades 

---

## 🧩 1. Instalar dependencias básicas

```bash
sudo apt update
sudo apt install -y zsh git curl wget unzip fonts-powerline
```

---

## 💎 2. Instalar Oh My Posh (prompt moderno)

```bash
sudo wget https://github.com/JanDeDobbeleer/oh-my-posh/releases/latest/download/posh-linux-amd64 -O /usr/local/bin/oh-my-posh
sudo chmod +x /usr/local/bin/oh-my-posh
```

Verifica la instalación:

```bash
oh-my-posh --version
```

---

## ⚙️ 3. Instalar Oh My Zsh (framework para Zsh)

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

Si el instalador reemplaza tu `.zshrc`, vuelve a aplicar tu **symlink**:

```bash
rm ~/.zshrc
ln -s ~/.config/zshrc/zshrc/.zshrc ~/.zshrc
```

---

## 🔌 4. Plugins recomendados

```bash
# Sugerencias en tiempo real
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

# Resaltado de sintaxis clásico
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting

# Resaltado de sintaxis rápido
git clone https://github.com/zdharma-continuum/fast-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/fast-syntax-highlighting
```

---

## ⚡ 5. Utilidades adicionales

```bash
sudo apt install -y fzf eza
```

- **fzf** → buscador interactivo para historial, archivos, etc.  
- **eza** → reemplazo moderno de `ls`, con íconos y colores.

---

## 🧠 6. (Opcional) Instalar Nerd Fonts

Para mostrar íconos correctamente:

```bash
mkdir -p ~/.local/share/fonts
cd ~/.local/share/fonts
wget https://github.com/ryanoasis/nerd-fonts/releases/latest/download/FiraCode.zip
unzip FiraCode.zip && rm FiraCode.zip
fc-cache -fv
```

Luego en tu terminal (por ejemplo **Kitty** o **Alacritty**), selecciona:

```
font_family FiraCode Nerd Font
```

---

## 🧩 7. Activar Zsh como shell predeterminado

```bash
chsh -s $(which zsh)
```

Cierra la sesión o reinicia la terminal para aplicar los cambios.

---

## 📂 8. Estructura de configuración esperada

```bash
~/.config/zshrc/
 ├─ 00-init
 ├─ 20-customization
 ├─ 25-aliases
 ├─ 30-autostart
 ├─ ohmyposh/
 │   ├─ zen.toml
 │   └─ EDM115-newline.omp.json
 └─ zshrc/
     ├─ .zshrc
     └─ .zshrc.pre-oh-my-zsh
```

Crea el **symlink** necesario:

```bash
ln -s ~/.config/zshrc/zshrc/.zshrc ~/.zshrc
```

---

## 🎨 9. Terminal recomendada (Kitty)

Instala y selecciona **Kitty** como terminal predeterminada:

```bash
sudo apt install kitty
sudo update-alternatives --config x-terminal-emulator
```

Selecciona `kitty` en la lista.

---

## ✅ 10. Verificación final

Abre una nueva terminal y comprueba:

```bash
zsh --version
oh-my-posh --version
eza --version
fzf --version
```

---

### 💡 Listo
Tu entorno Zsh modular está configurado.  
Disfruta de una terminal rápida, moderna y completamente personalizable 🚀
