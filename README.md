# focus: macos app & website blocker (daemonized)
Temporarily blocks distracting apps and websites in the background.

---

## Overview
```
Usage: focus [commands] [options] [duration]
       focus [blocklist commands] <App Name | Website URL>
       
       App Names should match the name of the app as it appears in the mac's Applications folder.
       So, App Names are Case Sensitive (It's WhatsApp, not Whatsapp)

       And Website URLs should be in the format of "example.com" (without "https://").


Commands:
  start [--hard <n>] <dur>   Start the focus session (sudo required for website blocking)
  stop                       Stop the active focus session (sudo required for website blocking)
  status                     Check the status of the active focus session
  list                       List blocked apps and sites
  add <App>                  Add an app to the blocklist
  remove <App>               Remove an app from the blocklist
  add-site <URL>             Add a website to the blocklist
  remove-site <URL>          Remove a website from the blocklist

Options:
  --hard <num-of-chars>      Require typing random chars to stop early
  -h | --help                Show help message

Duration formats:
  5      (5 seconds)
  10s    (10 seconds)
  2m     (2 minutes)
  1h     (1 hour)

Examples:
  # Add YouTube to the website blocklist
  focus add-site "youtube.com"

  # Add Google Chrome to the app blocklist
  focus add "Google Chrome"

  # Add WhatsApp to the app blocklist
  focus add "WhatsApp"    # It's WhatsApp, not Whatsapp (Whatsapp won't work)

  # Start a focus session for 45 minutes
  # Note: sudo is required if you have websites in your blocklist
  sudo focus start 45m

  # Start a hard focus session for 1 hour (requires typing 100 random chars to stop early)
  sudo focus start --hard 100 1h

  # Check session status
  focus status

  # Stop the focus session early
  # Note: sudo is required if you have websites in your blocklist
  sudo focus stop
```
---

## Installation & Setup
1. **Clone the repository and cd into the directory**:
   ```bash
   git clone https://github.com/taraqfarhan/focus
   cd focus
   ```

2. **Make the script executable**:
   ```bash
   chmod +x focus
   ```

3. **Add to PATH**:
   To use the `focus` command globally, symlink it to a directory in your shell's path (such as `/usr/local/bin`):
   ```bash
   ln -s "$(pwd)/focus" /usr/local/bin/focus
   ```

4. **Enable Accessibility Permissions**:
   To query and control applications, macOS may request permissions.
   - Open **System Settings > Privacy & Security > Accessibility**.
   - Ensure your terminal application (e.g., Terminal, iTerm2, VS Code) is enabled in the list.
