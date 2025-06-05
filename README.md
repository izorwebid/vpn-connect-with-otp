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
