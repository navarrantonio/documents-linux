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
#### We see that we have five columns:

* UNIT: the name of the service configuration unit.
* LOAD: indicates whether the configuration unit has been loaded or not.
* ACTIVE: indicates whether the configuration unit is active or not.
* SUB: indicates in more detail if the configuration unit is running and what its current state is.
* DESCRIPTION: a short description of the configuration unit.
Since we are using the sudo systemctl list-units command that shows only active units or services, the values ​​in the LOAD column will always be loaded and those in the ACTIVE column will always be active. This way of showing services is what we get by default when we run the systemctl command without any option.

### Service management with systemctl
To administer services we will use the systemctl command:

#### List all active services (running) of the system
````bash
$ systemctl list-units --type service

#### List all active and inactive services
systemctl list-units --type service --all

#### Start, stop or restart a service
systemctl start name.service
systemctl stop name.service
systemctl restart name.service

#### Restart only if the service is already started
systemctl try-restart name.service

#### Reload configuration
systemctl reload name.service

#### Check the status of a service or if it is enabled (enabled)
systemctl status name.service
systemctl is-enabled name.service

#### Check if a service is activated (running)
systemctl is-active name.service

#### Enable a service (to start when the system starts)
systemctl enable name.service

#### Disable service
systemctl disable name.service

#### Kill a service (default SIGTERM)
systemctl kill name.service

#### We can specify the signal we send to do the kill with -s.
* For example send SIGKILL
systemctl kill -s SIGKILL name.service
````
* The amount of signals that we can pass to the kill option would give for an entire article.
  We can also do a reboot, halt or shutdown of the system:
  ````bash
  $ systemctl reboot 
  $ systemctl halt
  $ systemctl poweroff
  ````
  * To mention two interesting options
  
  ````bash
               mask
  $ systemctl mask nombre.service
              Unmask
  $ $ systemctl unmask nombre.service
  ````
  * When we mask a service, we not only disable it, but we also prevent it from being started manually or automatically.

In another order of things, we can analyze the start time of each of the services when starting the system with systemd-analyze blame:
````bash
  $ systemd-analyze blame
  ````
  https://www.digitalocean.com/community/tutorials/systemd-essentials-working-with-services-units-and-the-journal

 
 
