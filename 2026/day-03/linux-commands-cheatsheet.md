Process Managment commands

  Command                                What it does
  -------------------------------------- -----------------------------------
  `top`                                  Live view of processes, CPU, and memory

  `htop`                                 Friendlier interactive process viewer, if installed

  `ps -ef`                               Lists processes

  `ps aux --sort=-%cpu \| head`          Shows processes using the most CPU

  `ps aux --sort=-%mem \| head`          Shows processes using the most memory

  `pstree -ap`                           Shows process parent/child relationships

  `free -h`                              Shows RAM and swap usage

  `uptime`                               Shows load averages; compare with CPU core count and historical baseline

  `lscpu`                                Shows CPU details

  `pidof process_name`                   Shows PIDs for a process name, if available

  `lsof -p PID`                          Lists files/sockets opened by a process, 

  `kill PID`                             Sends SIGTERM by default, asking a process to stop gracefully

  `kill -TERM PID`                       Explicit graceful termination signal

  `kill -KILL PID`                       Forcefully terminates a process; use only if graceful termination fails

  `kill -STOP PID`                       Suspends a process

  `kill -CONT PID`                       Resumes a suspended process

  `jobs -l`                              Lists jobs started from the current shell

  `bg %1`                                Resumes job 1 in the background

  `fg %1`                                Brings job 1 to the foreground

  `nohup command > command.log 2>&1 &`   Starts a command intended to keep running after logout

  `nice -n 10 command`                   Starts a process with a lower scheduling priority

  `renice 10 -p PID`                     Changes a process's scheduling priority
  --------------------------------------------------------------------------

**Process troubleshooting sequence:** `uptime` → `free -h` → `top` →`p` sorted by CPU/memory → inspect the affected service's logs. High load does not automatically mean CPU is the only problem; tasks stuck in I/O can contribute.



 Filesystems Commands
 
 -----------------------------------------------------------------------
  Command                              What it does
  ------------------------------------ -----------------------------------
  `df -h`                              Checks filesystem space

  `df -i`                              Checks inode availability

  `du -xhd1 /path`                     Summarizes directory sizes on one
                                       filesystem (GNU `du`)
   x-Stay on one filesystem.
   d1 --Shows only the folders directly inside the path, not deeper levels. 
  'du -sh /path'			" "

  `lsblk -f`                           Lists block devices, filesystem
                                       types, labels, and UUIDs

  `findmnt`                            Shows mounted filesystems and mount
                                       relationships

  `mount`                              Shows current mounts when run
                                       without arguments

  `findmnt /mountpoint`                Checks what is mounted at a path

  `cat /etc/fstab`                     Shows persistent mount
                                       configuration

  `lsof +L1`                           Finds open deleted files that may
                                       still consume space, if installed

  `sudo journalctl --disk-usage`       Shows journal disk usage

  `free -h`                            Shows memory and swap usage
  ------------------------------------------------------------------------
 
 Networking commands
 
 A. Check your own network setup
 
 1. ip a - Shows IP addresses and network interfaces (newer replacement for ifconfig)
 2. ip route - Shows the routing table and default gateway
 3. hostname -I - Prints just the server’s IP addresses
 4. cat /etc/resolv.conf - Shows which DNS servers the machine uses
 
 B. Check if a host is reachable
 
 1. ping google.com      -   # is the host reachable? (Ctrl+C to stop)
 2. ping -c 4 google.com  -   # send only 4 packets
 3. traceroute google.com -   # shows each hop the packet takes
 traceroute helps find where the connection breaks along the path.
 
 C. Check DNS
 
 1. nslookup google.com      # basic DNS lookup
 2. dig google.com           # detailed DNS answer
 3. dig +short google.com    # only the IP
 
 D. Check ports and connections
 
 1. ss -tulpn                # which ports are listening, and which process owns them
 2. nc -zv server01 443      # is port 443 open on that server?
 3. telnet server01 443      # older way to test a port
 
 For ss -tulpn: t = TCP, u = UDP, l = listening, p = process, n = numbers instead of names. Use sudo to see the process names.
 
 E. Test web endpoints (very useful in CI/CD)
 
 1. curl https://example.com                 # fetch a page
 2. curl -I https://example.com              # headers only (check status code)
 3. curl -v https://example.com              # verbose: shows the TLS and connection steps
 4. curl -o /dev/null -s -w "%{http_code}\n" https://example.com   # just the status code
 5. wget https://example.com/file.zip        # download a file
 
 The status-code one is handy for health checks after a deployment.
 
 F. Capture and scan
 
 1. sudo tcpdump -i eth0 port 80     # capture live traffic
 2. nmap server01                    # scan open ports on a host
 
 G. Firewall

 1. sudo ufw status          # Ubuntu firewall
 2. ≥,sudo iptables -L         # low-level firewall rules