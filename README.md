# Privacy Quick Tips by Ghostio-cmd 🔒

Welcome to my personal collection of **quick, impactful tips** designed to help you boost your digital privacy and security, right now.

In a world where our data is constantly scrutinized, taking small, consistent steps can make a huge difference. This repository is my vault of practical advice – from browser tweaks to operating system settings, and everyday habits that safeguard your digital freedom.

My goal is to share straightforward insights that you can implement without needing to be a tech guru. Let's make privacy a habit!

## How to Use These Tips

Just scroll down! I've organized the tips into clear categories. Each one is designed to be concise, offering clear instructions and explaining *why* it matters. I'll be adding more as I discover them.

## 💡 Browse & Online Habits

### Enable DNS over HTTPS (DoH) in Your Browser
Encrypt your DNS queries to prevent your Internet Service Provider (ISP) or others from seeing which websites you're trying to visit.
* **Why it matters:** Traditional DNS queries are often unencrypted. DoH adds a layer of encryption, making your Browse more private and secure.
* **How:**
    * **Firefox:** Settings -> Search "DNS over HTTPS" -> Enable and choose a privacy-focused provider (e.g., Cloudflare, NextDNS).
    * **Chrome/Chromium:** Settings -> "Privacy and security" -> "Security" -> "Use secure DNS" -> Enable and select a provider.

### Use a Dedicated Browser for Sensitive Tasks
Keep your banking, email, and other critical accounts separate from your general Browse.
* **Why it matters:** This creates a sandboxed environment, minimizing the risk of tracking or cross-site contamination from everyday Browse.
* **How:** Choose a privacy-focused browser (like Firefox Focus or Brave) and dedicate it solely to sensitive logins.

### Regularly Clear Browser Cookies for Specific Sites
Don't clear *all* cookies if you don't want to log back into everything, but target sites that track heavily.
* **Why it matters:** Cookies can be used for persistent tracking across sessions. Clearing them limits how long sites can follow you.
* **How:** In your browser settings, look for "Site Data" or "Manage Data." You can selectively remove cookies for specific websites.

### Review and Manage Browser Extension Permissions
Extensions can be powerful, but they also often request broad permissions.
* **Why it matters:** Over-permissive extensions can track your Browse, inject ads, or even steal data. Only grant necessary permissions.
* **How:** Go to your browser's extension manager (e.g., `about:addons` in Firefox, `chrome://extensions` in Chrome). Click on each extension to review its permissions and disable any that seem excessive for its function. Consider removing extensions you don't actively use.

## 🐧 Operating System Hardening (Linux Focus)

### Set Up a Basic UFW Firewall
A simple firewall can block unwanted incoming connections to your system.
* **Why it matters:** It's your first line of defense against network-based attacks and helps control what communicates with your PC.
* **How:** On Ubuntu/Debian-based systems:
    ```bash
    sudo ufw enable          # Turns on the firewall
    sudo ufw default deny incoming # Blocks all incoming connections by default
    sudo ufw allow outgoing    # Allows all outgoing connections (for your internet use)
    sudo ufw status verbose    # Check status
    ```
    *Only open ports you explicitly need, like SSH if accessing remotely.*

### Check for Unnecessary Background Services
Many Linux distros come with services running that you might not need. Disabling them reduces your attack surface.
* **Why it matters:** Unused services can consume resources and potentially expose vulnerabilities.
* **How:** Use `systemctl list-unit-files --type=service` to see running services. Research any unfamiliar ones and use `sudo systemctl disable [service-name]` and `sudo systemctl stop [service-name]` if you're sure you don't need them.

### Use Flatpaks for App Sandboxing
Install applications as Flatpaks when possible to isolate them from the rest of your system.
* **Why it matters:** Flatpaks run apps in a sandbox, limiting their access to your file system and other system resources, significantly improving privacy and security.
* **How:** Ensure Flatpak is installed (`sudo apt install flatpak`), then add Flathub (`flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo`). Install apps with `flatpak install flathub [app-id]`. Review app permissions with `flatpak permissions`.

### Enable Full Disk Encryption (FDE)
Encrypt your entire hard drive to protect all your data if your device is lost or stolen.
* **Why it matters:** Without FDE, someone with physical access to your device can bypass your login and access your files. Encryption renders your data unreadable.
* **How:** Most Linux distributions offer FDE as an option during the installation process (often labeled as "Encrypt the new Ubuntu installation" or similar with LUKS). It's crucial to set this up *during* installation.

## 🔐 App & Account Security

### Implement Unique Passwords with a Manager
Never reuse passwords. Use a strong, unique password for every single account.
* **Why it matters:** If one service is breached, your other accounts remain secure. Password managers make this easy.
* **How:** Choose a reputable **password manager** (like Bitwarden, Proton Pass, or KeePassXC) and use it to generate and store complex, unique passwords for all your online services.

### Review App Permissions Regularly
Even privacy-focused apps might request permissions you don't want to grant.
* **Why it matters:** Apps can collect data or perform actions based on the permissions you grant them. Regularly checking helps ensure they only have necessary access.
* **How:** On Linux, for Flatpaks, use `flatpak permissions` or a GUI tool like Flatseal. For other apps, consult their settings or system-level permission managers.

### Disable Read Receipts in Messaging Apps
Control who knows when you've seen their messages.
* **Why it matters:** Read receipts give others information about your activity and availability that you might prefer to keep private.
* **How:** Most messaging apps (Signal, Telegram, WhatsApp, etc.) have an option in their privacy settings to disable read receipts. Find it and toggle it off.

### Enable Multi-Factor Authentication (MFA/2FA) Everywhere Possible
Add an extra layer of security beyond just your password.
* **Why it matters:** Even if your password is stolen, MFA prevents unauthorized access to your account without the second factor (e.g., a code from an authenticator app, a physical key).
* **How:** Look for "Security" or "Login" settings in your online accounts (email, social media, banking). Use authenticator apps (like Aegis, Authy) over SMS-based 2FA when available, as SMS can be vulnerable to SIM-swapping attacks.

## 🗄️ File & Data Management

### Securely Delete Sensitive Files
Don't just hit 'delete'; files often remain recoverable.
* **Why it matters:** When you "delete" a file, the operating system usually just marks the space as available, but the data itself remains until overwritten. Secure deletion ensures it's truly gone.
* **How:** Use a dedicated file shredder tool like **BleachBit** (`bleachbit` in Linux repos) or a command-line tool like `shred` (e.g., `shred -zufv [filename]`). For entire disks, consider a full disk wipe utility.

### Encrypt Sensitive Files and Folders
For individual files you want to protect, encryption adds an extra layer of security.
* **Why it matters:** Even if your system is accessed, encrypted files remain unreadable without the passphrase.
* **How:** Use tools like **GnuPG (GPG)** for individual files (`gpg -c [filename]`) or consider creating encrypted containers/vaults with tools like **VeraCrypt** for sensitive folders.

### Regularly Backup Your Data (and Encrypt Backups!)
Protect against data loss, but ensure your backups remain private.
* **Why it matters:** Data loss can happen due to hardware failure, malware, or accidental deletion. Encrypted backups ensure your sensitive information isn't exposed if the backup media falls into the wrong hands.
* **How:** Use backup solutions that offer encryption (e.g., **Duplicati**, or simply encrypt the backup drive/folder with **LUKS** or GPG before copying files). Store backups offline and in a separate physical location.

## Want to contribute a tip or have a question?

Feel free to [open an issue here](https://github.com/Ghostio-cmd/privacy-quick-tips/issues)!
