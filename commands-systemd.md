# systemd

#### To list all the active units managed by systemd execute the command:
````bash
$ sudo systemctl list-units
sudo systemctl list-units
[sudo] password for antonio:        
UNIT                               LOAD   ACTIVE SUB       DESCRIPTION
proc-sys-fs-binfmt_misc.automount  loaded active waiting   Arbitrary Executable File Formats 
sys-devices-pci0000:00-0000:00:02.0-backlight-acpi_video0.device loaded active plugged   /sys
sys-devices-pci0000:00-0000:00:1b.0-sound-card0.device loaded active plugged   7 Series/C210 
sys-devices-pci0000:00-0000:00:1c.2-0000:02:00.0-net-wlp2s0.device loaded active plugged   Ce
sys-devices-pci0000:00-0000:00:1c.3-0000:03:00.2-net-enp3s0f2.device loaded active plugged   
sys-devices-pci0000:00-0000:00:1f.2-ata1-host0-target0:0:0-0:0:0:0-block-sda-sda1.device load
sys-devices-pci0000:00-0000:00:1f.2-ata1-host0-target0:0:0-0:0:0:0-block-sda-sda2.device load
sys-devices-pci0000:00-0000:00:1f.2-ata1-host0-target0:0:0-0:0:0:0-block-sda-sda5.device load
sys-devices-pci0000:00-0000:00:1f.2-ata1-host0-target0:0:0-0:0:0:0-block-sda.device loaded ac
sys-devices-pci0000:00-0000:00:1f.2-ata1-host0-target0:0:1-0:0:1:0-block-sr0.device loaded ac
sys-devices-platform-coretemp.0-hwmon-hwmon1.device loaded active plugged   /sys/devices/plat
sys-devices-platform-serial8250-tty-ttyS0.device loaded active plugged   /sys/devices/platfor
sys-devices-platform-serial8250-tty-ttyS1.device loaded active plugged   /sys/devices/platfor
sys-devices-platform-serial8250-tty-ttyS10.device loaded active plugged   /sys/devices/platfo
sys-devices-platform-serial8250-tty-ttyS11.device loaded active plugged   /sys/devices/platfo
sys-devices-platform-serial8250-tty-ttyS12.device loaded active plugged   /sys/devices/platfo
sys-devices-platform-serial8250-tty-ttyS13.device loaded active plugged   /sys/devices/platfo
sys-devices-platform-serial8250-tty-ttyS14.device loaded active plugged   /sys/devices/platfo
sys-devices-platform-serial8250-tty-ttyS15.device loaded active plugged   /sys/devices/platfo
sys-devices-platform-serial8250-tty-ttyS16.device loaded active plugged   /sys/devices/platfo

````
