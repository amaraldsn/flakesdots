### ⬇️ Install

#### 📜 Script:

This is the easiest and recommended way of starting out. The script is not meant to allow you to change every option that you can in the flake or help you install extra packages. It is simply here so you can get my configuration installed with as little chances of breakages and then fiddle to your hearts content!

Simply copy this and run it:

```
nix-shell -p git curl
sh <(curl -L https://gitlab.com/Zaney/zaneyos/-/raw/main/install-zaneyos.sh)
```

#### 🦽 Manual:

Run this command to ensure Git & Vim are installed:

```
nix-shell -p git vim
```

Clone this repo & enter it:

```
git clone https://gitlab.com/amaraldsn/flakesdots.git
cd zaneyos
```

- *You should stay in this folder for the rest of the install*

Create the host folder for your machine(s)

```
cp -r hosts/default hosts/<your-desired-hostname>
```

**🪧🪧🪧 Edit options.nix 🪧🪧🪧**

Generate your hardware.nix like so:

```
nixos-generate-config --show-hardware-config > hosts/<your-desired-hostname>/hardware.nix
```

Configurar o arquivo flake.nix, e trocar o username e a arquitetura

```
vim flake.nix
```

Se alguma dependência falhar, ir no arquivo config.nix e retirar a instalação.

Run this to enable flakes and install the flake replacing hostname with whatever you put as the hostname:

```
NIX_CONFIG="experimental-features = nix-command flakes" 
sudo nixos-rebuild switch --flake .#hostname
```

Now when you want to rebuild the configuration you have access to an alias called flake-rebuild that will rebuild the flake!

Hope you enjoy!
