# focus: macos app & website blocker (daemonized)
Temporarily blocks distracting apps and websites in the background.

---

## Overview
```
Usage: focus [commands] [duration]
       focus [blocklist commands] <App Name | Website URL>

  focus add "safari"
  focus remove "safari"
  focus add-site "reddit.com"
  focus remove-site "reddit.com"

  focus start 1h
  focus stop
  focus status
  focus list
  focus -h | --help

Commands:
  add <App>             Add an app to the blocklist
  remove <App>          Remove an app from the blocklist
  add-site <URL>        Add a website to the blocklist
  remove-site <URL>     Remove a website from the blocklist
  start <duration>      Start the focus session (sudo required for website blocking)
  stop                  Stop the active focus session (sudo required for website blocking)
  status                Check the status of the active focus session
  list                  List blocked apps and sites
  -h | --help           Show help message

Duration formats:
  5      (5 seconds)
  10s    (10 seconds)
  2m     (2 minutes)
  1h     (1 hour)

Examples:
  # Add YouTube to the website blocklist
  focus add-site "youtube.com"

  # Add Discord to the app blocklist
  focus add "Discord"

  # Start a focus session for 45 minutes
  # Note: sudo is required if you have websites in your blocklist
  sudo focus start 45m

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

5. **Website Blocking & Sudo Access**:
   Modifying website blocklists edits `/etc/hosts` to route traffic to `127.0.0.1`.
   - Modifying `/etc/hosts` requires root privileges.
   - When launching a session that blocks websites, run with `sudo`:
     ```bash
     sudo focus start <duration>
     ```
     To stop a session that blocks websites:
     ```bash
     sudo focus stop
     ```
