# Node Sensor

The Node Sensor exposes a wide variety of hardware- and kernel-related metrics.

> ***NOTE:*** While the NIX-Node Sensor is for *nix systems, there is the Windows exporter for Windows that serves an analogous purpose.

## Installing and running the Node Sensor

To start with, you need to run Promethius Node Exporter

```bash
wget https://github.com/prometheus/node_exporter/releases/download/v*/node_exporter-*.*-amd64.tar.gz
tar xvfz node_exporter-*.*-amd64.tar.gz
cd node_exporter-*.*-amd64
./node_exporter
```

Then you run the NIX-Node Sensor

```bash
docker run -d metrasensor/node-sensor:latest \
    --name nix-node-sensor \
    --env PROJECT_UUID=<your_project_uuid> \
    --env SENSOR_NAME=<your_sensor_name> \
    --env PROMETHEUS_HOST=http://<prometheus_host>:9100/metrics \
```

## Node Exporter Collectors

There is varying support for collectors on each operating system. The tables
below list all existing collectors and the supported systems.

Collectors are enabled by providing a `--collector.<name>` flag.
Collectors that are enabled by default can be disabled by providing a `--no-collector.<name>` flag.

### Enabled by default

Name     | Description | OS
---------|-------------|----
arp | Exposes ARP statistics from `/proc/net/arp`. | Linux
bcache | Exposes bcache statistics from `/sys/fs/bcache/`. | Linux
bonding | Exposes the number of configured and active slaves of Linux bonding interfaces. | Linux
boottime | Exposes system boot time derived from the `kern.boottime` sysctl. | Darwin, Dragonfly, FreeBSD, NetBSD, OpenBSD, Solaris
conntrack | Shows conntrack statistics (does nothing if no `/proc/sys/net/netfilter/` present). | Linux
cpu | Exposes CPU statistics | Darwin, Dragonfly, FreeBSD, Linux, Solaris
cpufreq | Exposes CPU frequency statistics | Linux, Solaris
diskstats | Exposes disk I/O statistics. | Darwin, Linux, OpenBSD
edac | Exposes error detection and correction statistics. | Linux
entropy | Exposes available entropy. | Linux
exec | Exposes execution statistics. | Dragonfly, FreeBSD
filefd | Exposes file descriptor statistics from `/proc/sys/fs/file-nr`. | Linux
filesystem | Exposes filesystem statistics, such as disk space used. | Darwin, Dragonfly, FreeBSD, Linux, OpenBSD
hwmon | Expose hardware monitoring and sensor data from `/sys/class/hwmon/`. | Linux
infiniband | Exposes network statistics specific to InfiniBand and Intel OmniPath configurations. | Linux
ipvs | Exposes IPVS status from `/proc/net/ip_vs` and stats from `/proc/net/ip_vs_stats`. | Linux
loadavg | Exposes load average. | Darwin, Dragonfly, FreeBSD, Linux, NetBSD, OpenBSD, Solaris
mdadm | Exposes statistics about devices in `/proc/mdstat` (does nothing if no `/proc/mdstat` present). | Linux
meminfo | Exposes memory statistics. | Darwin, Dragonfly, FreeBSD, Linux, OpenBSD
netclass | Exposes network interface info from `/sys/class/net/` | Linux
netdev | Exposes network interface statistics such as bytes transferred. | Darwin, Dragonfly, FreeBSD, Linux, OpenBSD
netstat | Exposes network statistics from `/proc/net/netstat`. This is the same information as `netstat -s`. | Linux
nfs | Exposes NFS client statistics from `/proc/net/rpc/nfs`. This is the same information as `nfsstat -c`. | Linux
nfsd | Exposes NFS kernel server statistics from `/proc/net/rpc/nfsd`. This is the same information as `nfsstat -s`. | Linux
pressure | Exposes pressure stall statistics from `/proc/pressure/`. | Linux (kernel 4.20+ and/or [CONFIG\_PSI](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/Documentation/accounting/psi.txt))
rapl | Exposes various statistics from `/sys/class/powercap`. | Linux
schedstat | Exposes task scheduler statistics from `/proc/schedstat`. | Linux
sockstat | Exposes various statistics from `/proc/net/sockstat`. | Linux
softnet | Exposes statistics from `/proc/net/softnet_stat`. | Linux
stat | Exposes various statistics from `/proc/stat`. This includes boot time, forks and interrupts. | Linux
textfile | Exposes statistics read from local disk. The `--collector.textfile.directory` flag must be set. | _any_
thermal\_zone | Exposes thermal zone & cooling device statistics from `/sys/class/thermal`. | Linux
time | Exposes the current system time. | _any_
timex | Exposes selected adjtimex(2) system call stats. | Linux
udp_queues | Exposes UDP total lengths of the rx_queue and tx_queue from `/proc/net/udp` and `/proc/net/udp6`. | Linux
uname | Exposes system information as provided by the uname system call. | Darwin, FreeBSD, Linux, OpenBSD
vmstat | Exposes statistics from `/proc/vmstat`. | Linux
xfs | Exposes XFS runtime statistics. | Linux (kernel 4.4+)
zfs | Exposes [ZFS](http://open-zfs.org/) performance statistics. | [Linux](http://zfsonlinux.org/), Solaris

*[More information about Node Exporter](https://prometheus.io/docs/guides/node-exporter/)