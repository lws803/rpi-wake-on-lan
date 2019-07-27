# rpi-wake-on-lan
Raspberry Pi as wake on LAN server  

What you'll need:
1. 1x Raspberry pi
2. 1x Desktop with WOL(wake on lan) enabled. Check your BIOS settings for that.


Steps to let RPi wake your desktop for you

1. Sign up for ngrok
2. Fill in information for self-emailing in `send_email.py`
3. Place python script at the root of both Desktop and RPi
4. Download ngrok and place it in `/opt/ngrok/` together with `ngrok.yml` after filling in your authtoken for both RPi and desktop
5. Place ngrok.service and email_service.serivce in both RPi and Desktop at `/lib/systemd/system`
6. Enable the services with
    ```bash
    $ sudo chmod 644 email_service.serivce
    $ sudo chmod 644 ngrok.serivce
    $ sudo systemctl daemon-reload
    $ sudo systemctl enable email_service.serivce ngrok.serivce
    ```
7. Reboot and ensure that the email is sent out together with your new ngrok host.
8. You can use your RPi to wake your desktop by using wake on lan. But keep your RPi turned on
