# AI Server MoTD (Message Of The Day)

Show information about your AI/Deep Learning server in a nice format, including GPU utilization and VRAM usage~

![235893377-a332234a-230b-42dd-aede-dd9f78018898 (2)](https://user-images.githubusercontent.com/48984123/235893948-2b259590-0a6d-49bb-9c7a-c2fb126e00f3.png)

## Installation

Clone the repository and cd into it
```bash
https://github.com/fedebotu/ai-server-motd.git && cd ai-server-motd
```
### Displaying

To display on login via SSH, copy the messages you want in `/etc/update-motd.d`.
For example, if you want to use `30-nvidia`:

```bash
sudo cp 30-nvidia /etc/update-motd.d/
```

The messages will be displayed in alphabetical order (eg. 10-*, 20-*...). 

### Testing
You may test if you MOTD (the dynamic part) works with
```bash
run-parts /etc/update-motd.d/
```
If some parts do not show, check if the permissions are set to 755 (`chmod 755 [FILE]`)

### Bugfix
If there is no display, you may check the following answer from [Stackoverflow](https://askubuntu.com/questions/1394600/motd-not-showing-up-on-ubuntu-21-10):
> The file in `/etc/ssh/sshd_config` needed to be set this line `UsePAM yes`. That allowed the interactive login to trigger the file `/etc/pam.d/sshd` that contained `session    optional     pam_motd.so  motd=/run/motd.dynamic` to run, which in turn ran the files in `/etc/update-motd.d/` to trigger my MOTD when I login.

Also, there may be no display in case of errors. Make sure to test as described above.

### Extra

To use the `10-hostname-color`, you may run the following on a Ubuntu server:
```bash
sudo apt-get install update-motd
sudo apt-get install -y figlet
sudo snap install lolcat-c
```

note that you need `snap` install with you can install with `sudo apt install snap`.

## Credits
https://github.com/yboetz/motd
https://github.com/bcyran/fancy-motd
... and ChatGPT ofc
