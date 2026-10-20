# 🐧 Arch Linux Production Command Book

A highly organized CLI reference for my HP EliteBook 830 G7. Contains standard diagnostics, back-end toolchains, distributed engineering labs, and everyday shortcuts.

- **GitHub Repository**: `https://github.com/salllman84/archlinuxCommands.git`
- **Machine**: HP EliteBook 830 G7 (Intel i5 10th Gen)
- **Primary Desktop**: Hyprland WM + Waybar

---

## 📂 1. Filesystem Navigation & Directory Control

*Use case: Browsing, organizing, and cleaning your directories safely.*

| Goal / Description | Command |
| :--- | :--- |
| Show my current location in the filesystem | `pwd` |
| List all files, sizes, hidden configuration files, and permissions | `ls -la` |
| Change directory to my user's personal home folder | `cd ~` |
| Go back/up one folder level | `cd ..` |
| View directory structure visually as a tree | `tree -L 2` |
| Create nested folder hierarchies | `mkdir -p ~/workspace/cpp/systems-starter/src` |
| Delete a file permanently (Be careful!) | `rm filename` |
| Force-delete a folder and everything inside it | `rm -rf foldername` |
| Find how much free space is left on my hard drive partitions | `df -h` |
| Show exact RAM & swap memory usage | `free -h` |

---

## 🌐 2. Network & Internet Configuration

*Use case: Testing connection, diagnosing ports, and managing interfaces.*

| Goal / Description | Command |
| :--- | :--- |
| Open interactive text-based menu to configure Wi-Fi / networks | `nmtui` |
| Show all network interfaces (IP addresses & adapters) | `ip a` |
| List available Wi-Fi networks in the terminal | `nmcli device wifi list` |
| Connect to a Wi-Fi network from the command line | `nmcli device wifi connect "WIFI_NAME" password "PASSWORD"` |
| Test internet speed & packets (ping 3 times) | `ping -c 3 google.com` |
| Find which processes are listening on what TCP/UDP ports | `sudo ss -tulpn` |
| Inspect all network endpoints & adapters currently online | `netstat -rn` |
| Capture and view network traffic on an interface (Diagnostics) | `sudo tcpdump -i wlan0` |

---

## 📦 3. System Package Management (pacman & yay)

*Use case: Installing, updating, and completely uninstalling programs.*

| Goal / Description | Command |
| :--- | :--- |
| Full system sync and upgrade (Update all programs) | `sudo pacman -Syu` |
| Install package from official Arch repository | `sudo pacman -S <package_name>` |
| Completely uninstall a package, its unneeded dependencies, and configs | `sudo pacman -Rns <package_name>` |
| Search official packages for a keyword | `pacman -Ss <keyword>` |
| Search, compile, and install from the community AUR repository | `yay -S <package_name>` |
| Completely uninstall and remove leftover AUR dependencies | `yay -Rns <package_name>` |
| Full cleaning of package download caches (Frees disk space) | `yay -Scc` |
| List and uninstall "orphan" package dependencies no longer used | `yay -Yc` |

---

## 💻 4. Process Management & Task Killer

*Use case: Monitoring running tasks and killing frozen apps.*

| Goal / Description | Command |
| :--- | :--- |
| Launch interactive system monitor (CPU cores, RAM, and tasks) | `htop` |
| List all processes containing a search keyword | `ps aux \| grep <keyword>` |
| Politely ask a program to stop & save state (Graceful exit) | `kill <PID>` (or `kill -15 <PID>`) |
| Instantly force-kill a frozen process (Immediate shutdown) | `kill -9 <PID>` |
| Kill all processes of a program by name (e.g., kill all firefox) | `pkill -9 firefox` |
| Show which files & ports are being held open by a process | `lsof -p <PID>` |

---

## 🛠️ 5. C++20 Systems Programming & Toolchain

*Use case: Building, compiling, and configuring distributed back-end binaries.*

| Goal / Description | Command |
| :--- | :--- |
| Generate standard GDB Debug build directories using CMake & Ninja | `cmake -B build -G Ninja -DCMAKE_BUILD_TYPE=Debug` |
| Run compiler to build/link my C++ project from workspace | `cmake --build build` |
| Generate specialized AddressSanitizer/UBSan build directory | `cmake -B build_asan -G Ninja -DCMAKE_BUILD_TYPE=Debug -DENABLE_ASAN=ON` |
| Compile the project using Sanitizer configs | `cmake --build build_asan` |
| Manually compile a single source file without CMake | `g++ -std=c++20 -O0 -g3 main.cpp -o app` |
| List installed compilers, debugger versions, and build engines | `g++ --version && clang --version && cmake --version` |

---

## 🔍 6. Diagnosing, Profiling & Crash Debugging (ASan, GDB)

*Use case: Catching memory leaks, analyzing trace logs, and debugging crashes.*

| Goal / Description | Command |
| :--- | :--- |
| Monitor performance and view trace logs inside the terminal | `strace -f -tt -T -y ./build/node_server` |
| Execute binary inside GDB with pretty-printed interactive output | `gdb ./build/node_server` |
| Check for memory leaks, invalid reads/writes, and pointer bugs | `valgrind --leak-check=full --track-origins=yes ./build/node_server` |
| Review system crashes / segfault core dumps captured by the OS | `coredumpctl list` |
| Instantly open the most recently crashed program directly inside GDB | `coredumpctl debug` |
| Benchmark CPU hardware performance counters and efficiency | `perf stat ./build/node_server` |

---

## 🌐 7. GitHub Collaboration & Repository Control

*Use case: Managing source code, connecting remotes, and pushing code.*

| Goal / Description | Command |
| :--- | :--- |
| Complete interactive 8-character CLI sign-in workflow | `gh auth login` |
| Configure git to automatically use GitHub session | `gh auth setup-git` |
| View your GitHub login status, username, and active token | `gh auth status` |
| Download and connect any repository into my folder | `gh repo clone <repo_name>` |
| Clone a repository via SSH without prompt | `git clone git@github.com:salllman84/archlinuxCommands.git` |
| Configure global identity name and email | `git config --global user.name "Name"` / `git config --global user.email "email"` |
| Show recent changes and state of the repository | `git status` |
| Stage changes, commit, and push updates to `main` branch | `git add . && git commit -m "Update" && git push -u origin main` |

---

## 📟 8. Multiplexing & Pane Control (tmux)

*Use case: Splitting a single terminal into multiple split panes.*

| Goal / Action | Command / Shortcut |
| :--- | :--- |
| Start/resume a multi-pane terminal session | `tmux` |
| Split terminal into left & right panes | `Ctrl + B` then `\|` (Vertical) |
| Split terminal into top & bottom panes | `Ctrl + B` then `-` (Horizontal) |
| Switch active pane without pressing prefix | `Alt + Arrow keys` |
| Exit current tmux pane/session | `exit` |

---

## ⌨️ 9. OS Hardware, Screen Backlight & volume Binds

*Use case: Controlling EliteBook function keys, volume, brightness, and captures.*

| Goal / Description | Command |
| :--- | :--- |
| Manually configure backlight brightness (e.g., set to 70%) | `brightnessctl set 70%` |
| Turn system volume up, down, or toggle mute | `wpctl set-volume -l 1.5 @DEFAULT_AUDIO_SINK@ 5%+` / `-` / `toggle` |
| Check status & mute status of digital microphones | `wpctl set-mute @DEFAULT_AUDIO_SOURCE@ toggle` |
| Capture full screen, save to Pictures, and copy to clipboard | `grim filename.png && wl-copy < filename.png` |
| Drag box to select and capture screen area, save and copy | `grim -g "$(slurp)" filename.png && wl-copy < filename.png` |

---

This is my dynamic reference. Run `git add . && git commit -m "update handbook" && git push` to sync any manual tweaks instantly.