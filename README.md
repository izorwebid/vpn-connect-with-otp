# VPN Connect with OTP (macOS Only)
This tool allows you to connect to OpenVPN configurations that require both a password and OTP (e.g., from Google Authenticator or similar).

### 🛠 Requirement:
```
brew install openvpn
brew install oath-toolkit
brew install terminal-notifier
```

### ⚙️ Setup
1. Place your VPN config file (`.ovpn`) into the `configs` directory.
Example: `uat.ovpn`, `local.ovpn`, etc.

2. Copy the environment example file and edit it:
```
cp .env.example .env
```
3. Then, edit .env with your VPN usernames and OTP secrets.

### 🚀 Make script executable
```
chmod +x ~/vpn-tool/vpn

#or

chmod +x /Users/your-user-name/path/to/vpn-tool/vpn
```
Replace `/Users/your-user-name/path/to` with your actual path

### ➕ Add to PATH:
If you use bash:
Add to your `~/.bash_profile` or `~/.bashrc`:
```
export PATH="$HOME/vpn-tool:$PATH"
```
If you use fish:
Add this function to `~/.config/fish/config.fish`:
```
function vpn
    bash /Users/your-user-name/path/to/vpn-tool/vpn $argv
end
```
Replace `/Users/your-user-name/path/to` with your actual path

### 🧪 Usage
Run in terminal:
```
vpn [uat|local|prod]
```

The argument should match your config filename (e.g., `uat.ovpn` → `vpn uat`).

Ensure your .env file includes `USERNAME_UAT` or `USERNAME_LOCAL` depending on your VPN target.



## 🔐 Optional: Allow VPN to Connect Without Password Prompt
To avoid being prompted for your macOS password each time the VPN connects, you can add a sudoers rule to allow openvpn to run without a password.

### ⚠️ Use with caution:
This gives permission to run openvpn as root without prompting for a password. Only use on a trusted machine.

### ➕ Add to sudoers:
1. Run:
```
sudo visudo
```
2. Add the following line at the bottom (replace `izorwebid` with your macOS username if different):
```
izorwebid ALL=(ALL) NOPASSWD: /usr/local/sbin/openvpn
```

3. Save and exit.
This assumes openvpn is installed at `/usr/local/sbin/openvpn`. You can confirm with:
```
which openvpn
```

