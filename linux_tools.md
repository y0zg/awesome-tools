# Linux Tools and Resources

Collection of Linux tools, commands, troubleshooting techniques

## System Administration

### Process Management

- [strace](https://strace.io/) - Trace system calls and signals
  - `strace -p PID` - Attach to running process
  - `strace uptime 2>&1 | grep lib` - Trace and filter output
  - `strace -f -e trace=network` - Trace network-related calls
- [lsof](https://linux.die.net/man/8/lsof) - List open files
  - `lsof -i :PORT` - Show processes using a specific port
- [ps](https://linux.die.net/man/1/ps) - Report process status
  - `ps aux | grep process_name` - Find specific processes
- [pgrep](https://linux.die.net/man/1/pgrep) - Find processes by name
- [pkill](https://linux.die.net/man/1/pkill) - Kill processes by name
- [atop](https://www.atoptool.nl/) - Advanced system and process monitor
- [traceloop](https://github.com/kinvolk/traceloop) - eBPF-based system call tracing
- [Parca](https://www.parca.dev/) - Continuous profiling for analysis

### File System Tools

- [dd](https://linux.die.net/man/1/dd) - Convert and copy files
  - `sudo ddrescue ubuntu-20.04-beta-desktop-amd64.iso /dev/sdb --force -D` - Create bootable USB
- [rsync](https://linux.die.net/man/1/rsync) - Fast file copying tool
- [find](https://linux.die.net/man/1/find) - Search for files
  - `find . -name "*.log" -mtime +7 -delete` - Delete old log files
- [namei](https://linux.die.net/man/1/namei) - Follow a pathname until a terminal point is found
  - Useful for checking permission issues along a path
- [ncdu](https://dev.yorhel.nl/ncdu) - Disk usage analyzer with ncurses interface
- [fsck](https://linux.die.net/man/8/fsck) - Check and repair a Linux filesystem
- [setfattr/getfattr](https://linux.die.net/man/1/setfattr) - Set/get extended file attributes
  ```bash
  setfattr -n user.checksum -v "3baf9ebce4c664ca8d9e5f6314fb47fb" file.txt
  getfattr -d file.txt
  ```

### Network Tools

- [ss](https://linux.die.net/man/8/ss) - Another utility to investigate sockets
- [ip](https://linux.die.net/man/8/ip) - Show/manipulate routing, devices, policy routing and tunnels
- [tcpdump](https://www.tcpdump.org/) - Dump traffic on a network
  - `tcpdump -i eth0 port 80 -w capture.pcap` - Capture HTTP traffic
- [netstat](https://linux.die.net/man/8/netstat) - Network statistics
- [socat](https://linux.die.net/man/1/socat) - Multipurpose relay (socket CAT)
  ```bash
  sudo socat TCP4-LISTEN:80,fork TCP4:localhost:3000
  ```
- [iptables](https://linux.die.net/man/8/iptables) - Administration tool for IPv4 packet filtering
- [curl](https://curl.se/) - Transfer data from or to a server
  - `curl -v https://example.com` - Verbose output showing headers

### Security

- [openssl](https://www.openssl.org/) - Toolkit for SSL/TLS
  - Self-signed certificate:
    ```bash
    openssl req -x509 -newkey rsa:4096 -keyout key.pem -out cert.pem -days 365
    ```
  - Convert certificate formats:
    ```bash
    openssl x509 -in cert.crt -out cert.pem -outform PEM
    ```
  - Check certificate details:
    ```bash
    openssl x509 -in cert.pem -text -noout
    ```
- [ssh-copy-id](https://linux.die.net/man/1/ssh-copy-id) - Install SSH key on a server
  ```bash
  ssh-copy-id user@hostname
  ```
- [sshpass](https://linux.die.net/man/1/sshpass) - Non-interactive SSH password authentication
- [pass](https://www.passwordstore.org/) - Standard Unix password manager
- [gopass](https://www.gopass.pw/) - Advanced password manager

### SSH Tricks

#### SSH Agent Forwarding
```bash
ssh -A user@host
```

#### SSH Port Forwarding

**Local Port Forwarding (access remote service locally)**
```bash
ssh -L local_port:remote_host:remote_port user@ssh_host
```

**Remote Port Forwarding (expose local service remotely)**
```bash
ssh -R remote_port:local_host:local_port user@ssh_host
```

#### SSH ProxyCommand (Bastion/Jump Server)
```
Host internal-server
  ProxyCommand ssh bastion-host -W %h:%p
```

## System Monitoring

- [htop](https://htop.dev/) - Interactive process viewer
- [iotop](https://linux.die.net/man/1/iotop) - Monitor I/O usage by processes
- [vmstat](https://linux.die.net/man/8/vmstat) - Report virtual memory statistics
- [smem](https://www.selenic.com/smem/) - Report memory usage accounting for shared libraries
- [blktrace/blkparse](https://linux.die.net/man/8/blktrace) - Block layer I/O tracing mechanism
- [eBPF tools](https://ebpf.io/) - Extended Berkeley Packet Filter tools for tracing and monitoring
  - [BCC Tools](https://github.com/iovisor/bcc) - BPF Compiler Collection

## Containerization & Isolation

### Namespaces and CGroups

- Control groups (cgroups) limit, account for, and isolate resource usage
  ```bash
  # Create a memory-limited cgroup
  mkdir -p /sys/fs/cgroup/memory/demo
  echo $PID > cgroup.procs
  echo 5000000 > memory.limit_in_bytes 
  ```

- Namespace isolation
  ```bash
  sudo unshare --fork --pid --mount-proc sh
  ```

### Container Building

- Minimal container example with chroot
  ```bash
  mkdir docker
  cp $(which ls) docker/bin/
  cp $(which bash) docker/bin/
  for lib in $(ldd /usr/bin/bash |grep -o -P '/\S+'); do cp $lib docker/lib64/; done
  for lib in $(ldd /usr/bin/ls |grep -o -P '/\S+'); do cp $lib docker/lib64; done
  ln -s lib64 lib
  sudo chroot docker /bin/bash
  ```

## System Configuration

### systemd

- Service management
  ```bash
  systemctl start/stop/restart/status service_name
  ```

- Viewing logs
  ```bash
  journalctl -u service_name
  ```

- Understanding unit file options
  ```
  [Unit]
  Description=Description of service
  After=network.target
  
  [Service]
  Type=simple/forking/oneshot
  ExecStart=/path/to/executable
  Restart=on-failure
  
  [Install]
  WantedBy=multi-user.target
  ```

- Difference between `systemctl disable` and `systemctl mask`
  - `disable` - Remove symlinks, can be started manually
  - `mask` - Symlink to /dev/null, cannot be started at all

### File Permissions

- Special permissions
  - SUID (4): Run as the file owner
  - SGID (2): Run with the group of the file
  - Sticky bit (1): Only file owner can delete

- Change permissions
  ```bash
  chmod u+x,g-w,o=r file  # User+execute, Group-write, Others=read
  ```

- Change ownership
  ```bash
  chown user:group file
  ```

- Find SUID binaries
  ```bash
  find / -perm -4000 -ls 2>/dev/null
  ```

## Shell Tips & Tricks

### Bash Shortcuts

- `sudo !!` - Run previous command with sudo
- `$_` - Last argument of previous command (e.g., `mkdir mydir && cd $_`)
- `[space] command` - Run command without saving in history
- `Ctrl+R` - Search command history
- `Ctrl+A/E` - Move to beginning/end of line

### Bash Parameter Expansion

- Use default value if variable is unset or empty
  ```bash
  ${CERT_PATH:-$PWD/certs}
  ```

- Check connection without telnet/nc
  ```bash
  timeout 1 bash -c "</dev/tcp/hostname/port"
  echo $?  # 0 for success
  ```

### Output Redirection

- Redirect with sudo permission
  ```bash
  sudo sh -c 'echo "content" >> /etc/protected_file'
  ```

- Named pipes
  ```bash
  mkfifo mypipe
  command1 > mypipe & command2 < mypipe
  ```

## Troubleshooting

### Debugging Techniques

- Check system logs
  ```bash
  dmesg
  less /var/log/syslog
  journalctl -xe
  ```

- Check disk space
  ```bash
  df -h
  du -h --max-depth=1 /path
  ```

- Investigate high load
  ```bash
  top
  vmstat 1
  iostat -x 1
  ```

- Debug bash scripts
  ```bash
  bash -x script.sh
  ```

### Filesystem Recovery

- Recover deleted files (if process still has them open)
  ```bash
  lsof | grep deleted
  # Find file descriptor in /proc/PID/fd/
  ```

- Fix corrupted filesystem
  ```bash
  # Boot to single user mode
  fsck -f /dev/sdXY
  ```

- Fix inaccessible /tmp directory
  ```bash
  # In single user mode
  mv /tmp /old.tmp
  mkdir /tmp
  chmod 1777 /tmp
  ```

## Additional Resources

- [Linux Load Average Explained](http://www.brendangregg.com/blog/2017-08-08/linux-load-averages.html)
- [Linux Capabilities](https://linux-audit.com/linux-capabilities-hardening-linux-binaries-by-removing-setuid/)
- [SSH Port Knocking](https://www.rapid7.com/blog/post/2017/10/04/how-to-secure-ssh-server-using-port-knocking-on-ubuntu-linux/)
- [SFTP User Setup](https://www.vultr.com/docs/setup-sftp-user-accounts-on-ubuntu-20-04/)
- [GoLinuxCloud Tutorials](https://www.golinuxcloud.com/) 