
# Kodak Brownie Model D

![Brownie Mode D](/images/brownie.png)

Converting old Kodak Brownie Model D camera to digital camera.

## Proof of Concept

Notes for proof of concept internals. This is more or less diary on what done.

The idea is to put Raspberry Pi inside the camera body. The PoC hardware:

- [Raspberry Pi 4  Model B](https://www.raspberrypi.org/products/raspberry-pi-4-model-b/)
- [Raspberry Pi Camera V2.1](https://www.raspberrypi.org/products/camera-module-v2/)

### Step 1: Prepare Raspberry Pi with OS

1. Get [Ubuntu 20.04 LTS 64bit](https://ubuntu.com/download/raspberry-pi). The Ubuntu Core
   image is smaller, but it is security hardened and maybe too locked down. Ubuntu server
   edition is suitable for PoC. It has SSH and Python available.
2. Make Raspberry Pi SD card
   ([tutorial](https://ubuntu.com/tutorials/create-an-ubuntu-image-for-a-raspberry-pi-on-ubuntu))
3. Connect Raspberry Pi to monitor and modify the system:
   - Change password for user ubuntu
   - Connect to network. Ubuntu Server has sshd running by default.
   - Install ssh key to enable passwordless ssh
     ([how-to](https://askubuntu.com/questions/46930/how-can-i-set-up-password-less-ssh-login)).
     Test connection.
   - Disable password based ssh loging by creating sshd config file
     `/etc/ssh/sshd_config.d/no_passwd.conf` with contents:

        ```
        # Disbale password based login and login as root
        ChallengeResponseAuthentication no
        PasswordAuthentication no
        UsePAM no
        PermitRootLogin no
        ```

      and reload sshd configs `systemctl reload sshd.service`

Now we have a system ready for hacking.

## Random Notes and Links

- https://ubuntu.com/blog/how-to-stream-video-with-raspberry-pi-hq-camera-on-ubuntu-core
- https://snapcraft.io/blog/easy-iot-with-ubuntu-core-and-raspberry-pi

