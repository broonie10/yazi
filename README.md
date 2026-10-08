# yazi

```bash
sudo apt install ffmpeg p7zip-full jq poppler-utils fd-find ripgrep fzf imagemagick unzip ueberzug chafa libsixel-bin


wget https://github.com/sxyazi/yazi/releases/latest/download/yazi-x86_64-unknown-linux-gnu.zip -O yazi.zip
ls -lh yazi.zip
unzip -q yazi.zip -d yazi-temp
sudo mv yazi-temp/*/{ya,yazi} /usr/local/bin
rm -rf yazi-temp yazi.zip
yazi --version
yazi

# Theme
ya pkg add yazi-rs/flavors:dracula

# Config
nvim ~/.config/yazi/theme.toml
[flavor]
dark = "dracula"


# Bashrc
# echo "alias yy='yazi'" >> ~/.bashrc
cat >> ~/.bashrc << 'EOF'
function yy() {
    local tmp="$(mktemp -t "yazi-cwd.XXXXXX")"
    yazi "$@" --cwd-file="$tmp"
    if cwd="$(cat -- "$tmp")" && [ -n "$cwd" ] && [ "$cwd" != "$PWD" ]; then
        builtin cd -- "$cwd"
    fi
    rm -f -- "$tmp"
}
EOF

# Source Bashrc
source ~/.bashrc

# Yazi
yy
```

# yazi-keybindings

```bash
Default Keybindings (Built-in)
All the essential shortcuts already work:

Help: ~
Navigation: h/j/k/l (vim-style) or arrow keys
Enter directory: l or Enter
Go back: h or Backspace
Search files: f (filter) or s (fd search)
Search content: S (ripgrep)
Toggle hidden: .
Copy files: y
Cut files: x
Paste: p
Delete: d
Rename: r
Create: a
Select: Space
Select all: Ctrl+a
Open: Enter or l
Shell command: :
Quit: q


```
