# HP-Servers

echo "deb http://downloads.linux.hpe.com/SDR/repo/mcp bionic/current non-free" > /etc/apt/sources.list.d/hp-mcp.list


wget -q -O - http://downloads.linux.hpe.com/SDR/hpPublicKey1024.pub | apt-key add -
wget -q -O - http://downloads.linux.hpe.com/SDR/hpPublicKey2048.pub | apt-key add -
wget -q -O - http://downloads.linux.hpe.com/SDR/hpPublicKey2048_key1.pub | apt-key add -
wget -q -O - http://downloads.linux.hpe.com/SDR/hpePublicKey2048_key1.pub | apt-key add -



# apt-get install hponcfg

Agentless Management Service (iLO 5) :

Agentless Management Service (AMSD) provides support for HPE Integrated Lights-Out 5 (HPE iLO 5) Embedded Health and Alerting.

# apt-get install amsd

Smart Storage Administrator (SSA)

If there is an older version of SSA  installed on the system, remove it first. To install the new version run:

apt-get install ssa

Smart Storage Administrator (SSA) CLI 

The Smart Storage Administrator CLI (SSACLI) is a commandline-based disk configuration program that helps you configure, manage, diagnose, and monitor Smart Array Controllers.

apt-get install ssacli

Smart Storage Administrator Diagnostic Utility (SSADU) CLI

The Smart Storage Administrator Diagnostic Utility CLI is a commandline-based disk configuration program for Smart Array Controllers

apt-get install ssaducli 

HPE MegaRAID Storage Administrator StorCLI (storcli)

StorCLI is a command line interface that enables multiple users to perform maintaining, troubleshooting, and configuration functions for the MegaRAID® Gen10 controller products

apt-get install storcli




Command examples
Here are few examples of ssacli commands that you can use to diagnose and manage your HP Smart Storage Controller.

Show available controllers

ssacli ctrl all show
Show controllers status

ssacli ctrl all show status
Show detailed controllers information

ssacli ctrl all show detail
Show controllers configuration

ssacli ctrl all show config
Rescan for new devices Useful after swapping disks in bays, etc...

ssacli rescan
Show all physical disks (or their status) (controller slot 0)

ssacli ctrl slot=0 pd all show
ssacli ctrl slot=0 pd all show status
Show all physical disks detailed information (controller slot 0)

ssacli ctrl slot=0 pd all show detail
Show logical drives (or their status) (controller slot 0, all or specific logical drive(s))

ssacli ctrl slot=0 ld all show
ssacli ctrl slot=0 ld all show status

ssacli ctrl slot=0 ld 1 show
ssacli ctrl slot=0 ld 1 show status
Show detailed logical drives information (controller slot 0, all or specific logical drive(s))

ssacli ctrl slot=0 ld all show detail
ssacli ctrl slot=0 ld 1 show detail
Show array information (controller slot 0, array A)

ssacli ctrl slot=0 array a show
Show array status (controller slot 0, all arrays)

ssacli ctrl slot=0 array all show status
Create new RAID 0 logical drive (controller slot 0, disk in port 1I:box 1:bay 1)

ssacli ctrl slot=0 create type=ld drives=1I:1:1 raid=0
Create new RAID 1 logical drive (controller slot 0, disks in port 1I:box 1:bay 1 and 2)

ssacli ctrl slot=0 create type=ld drives=1I:1:1,1I:1:2 raid=1
Create new RAID 5 logical drive (controller slot 0, diks in port 1I:box 1:bay 1 to 4)

ssacli ctrl slot=0 create type=ld drives=1I:1:1-1I:1:4 raid=5
Delete logical drive (controller slot 0, logical drive 1)

ssacli ctrl slot=0 ld 1 delete
Add new physical disks to logical drive (controller slot 0, logical drive 1, disks in port 1I:box 1:bay 6 and 7)

ssacli ctrl slot=0 ld 2 add drives=1I:1:6,1I:1:7
Add spare disks (controller slot 0, logical drive 1, array A, disks in port 1I:box 1:bay 6 and 7)

ssacli ctrl slot=0 array a add spares=1I:1:6,1I:1:7
Add global spare disks (controller slot 0, logical drive 1, all arrays, disks in port 1I:box 1:bay 6 and 7)

ssacli ctrl slot=0 array all add spares=1I:1:6,1I:1:7
Turn on/off blink logical drive LED (controller slot 0, logical drive 1)

ssacli ctrl slot=0 ld 1 modify led=on
ssacli ctrl slot=0 ld 1 modify led=off
Turn on/off blink physical disk LED (controller slot 0, physical disk port 1I:box 1:bay 1)

ssacli ctrl slot=0 pd 1I:1:1 modify led=on
ssacli ctrl slot=0 pd 1I:1:1 modify led=off
Modify smart array cache read and write ratio (controller slot 0, cacheratio 80% read/20% write)

ssacli ctrl slot=0 modify cacheratio=80/20
Show physical drive write cache status (controller slot 0)

ssacli ctrl slot=0 modify dwc=?
Enable/disable physical drive write cache (controller slot 0) Important: Because physical drive write cache is not battery-backed, you could lose data if a power failure occurs during a write process. To minimize this possibility, use a backup power supply.

ssacli ctrl slot=0 modify dwc=enable
ssacli ctrl slot=0 modify dwc=disable
Show status of smart array write cache when no battery is present (no-battery write cache option, controller slot 0)

ssacli ctrl slot=0 modify nbwc=?
Enable/disable smart array write cache when no battery is present (no-battery write cache option, controller slot 0)

ssacli ctrl slot=0 modify nbwc=enable
ssacli ctrl slot=0 modify nbwc=disable
Enable/disable smart array cache for certain Logical Volume (controller slot 0, logical drive 1)

ssacli ctrl slot=0 ld 1 modify arrayaccelerator=enable
ssacli ctrl slot=0 ld 1 modify arrayaccelerator=disable
Enable/disable SSD Smart Path (controller slot 0, array A)

ssacli ctrl slot=0 array a modify ssdsmartpath=enable
ssacli ctrl slot=0 array a modify ssdsmartpath=disable
Show spare activation mode

ssacli ctrl slot=0 modify spareactivationmode=?
Set spare activation mode

ssacli ctrl slot=0 modify spareactivationmode=predictive
ssacli ctrl slot=0 modify spareactivationmode=failure
Show rebuild priority

ssacli ctrl slot=0 modify rp=?
Modify rebuild priority

ssacli ctrl slot=0 modify rp=low
ssacli ctrl slot=0 modify rp=medium
ssacli ctrl slot=0 modify rp=mediumhigh
ssacli ctrl slot=0 modify rp=high
Erase Physical Drive (controller slot 0, physical disk port 1I:box 1:bay 1)

ssacli ctrl slot=0 pd 1I:1:1 modify erase
