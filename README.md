# Workstation tooling setup for Ubuntu-based workstations

## Prerequisite steps

- Install `task` CLI (see script below)
- Install `git-core` from `apt`, at minimum

## Graphical environment

- Install Vivaldi browser
- Uninstall other browsers (e.g., Firefox, Chrome, Edge, ...)
- Update "Favorites" in launch bar to include only the following, in this order:
  1. Web browser
  2. Terminal
  3. File manager
  4. VPN software (if any)

## Setup

From a clean workstation:

```bash
~/workspace $ curl -SsLo ./install-task.sh https://taskfile.dev/install.sh

# NOTE: Review contents of `install-task.sh`, just in case

~/workspace $ sh ./install-task.sh -d -b ~/.local/bin

go-task/task info checking GitHub for latest tag
go-task/task debug http_download https://github.com/go-task/task/releases/latest
go-task/task info found version: 3.42.1 for v3.42.1/linux/amd64
go-task/task debug downloading files into /tmp/tmp.kS0tB81wqT
go-task/task debug http_download https://github.com/go-task/task/releases/download/v3.42.1/task_linux_amd64.tar.gz
go-task/task debug http_download https://github.com/go-task/task/releases/download/v3.42.1/task_checksums.txt
go-task/task info installed ~/.local/bin/task

# Because `~/.local/bin` may not be in the PATH yet
~/workspace $ task="${HOME}/.local/bin/task"

~/workspace $ git clone https://github.com/TheLonelyGhost/dotfiles-ubuntu.git ~/.dotfiles

~/workspace $ "$task" --taskfile ~/.dotfiles/Taskfile.yml setup
```

This will invoke `task` to read the `Taskfile.yml` in the dotfiles repo.
