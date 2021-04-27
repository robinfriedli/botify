For Ubuntu 18.04 Systemd

You can run Botify as a service by creating the following .service file under
/etc/systemd/system

vi botify.service</br>
you can name the service file whatever you want to call it.

Than paste the following

[Unit] </br>
After=postgresql.service </br>
Description=Botify </br>
</br>
[Service]</br>
WorkingDirectory=/home/(your install dir)/botify</br>
ExecStart=/home/(your install dir)/botify/resources/bash/launch.sh</br>
Restart=always</br>
StandardOutput=file:/var/log/botify.log</br>
StandardError=file:/var/log/botify-error.log</br>
User=(Your User) </br>
Group=(Your Group) </br>
[Install]</br>
WantedBy=multi-user.target</br>


After you have created the file run the following command</br>
systemctl daemon-reload

If you want the service to run on boot run the following command</br>
systemctl enable botify
