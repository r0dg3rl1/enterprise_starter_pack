# Linux Troubleshooting Cheatsheet

## Gather Information

View all collected Journal entries. 
`journalctl`

View journal entries related to a specific device.
`journalctl </dev/sda>`

Filter journal logs for messages that relate to a specific systemd service or other type of systemd unit. 
`journalctl -b _SYSTEM_UNIT=http.service`

View logs for a single systemd service intance, through PID.
`journalctl -b _SYSTEMD_UNIT=<http.service> _PID=3326`

Show boot ids.
`journalctl --list-boots`

View info from a particular boot.
`journalctl --boot <boot_id> _SYSTEMD_UNIT=<http.service>`

RHEL 8 stores system journal logs in a ring buffer by default (/run/log/journal). 
To enable persistent storage of journal logs, create a disk directory and configure the journald service to use it.
e.g.
Create a disk directory.
`mkdir /var/log/journal`
Replace #Storage=auto to Storage=persistent (if applicable), so that persistent storage policy is configured.
`sed -i 's/#Storage=auto/Storage=persistent/' /etc/systemd/journald.conf`
Restart the systemd-journald service.
`systemctl restart systemd-journald.service`
* Note that if the configured directory does not exist or isn't writable by systemd-journald, then the service will continue to use the /run/log/journal location. 
