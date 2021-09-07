# Hardening-Debian

This is a guide to configuring and managing a domain and remote host with services such as VPN, obfuscated Tor bridge, Privoxy, Light Web Server, Docker, using the Debian GNU/Linux operating system and other free software.

This guide is written for OVH VPS running Debian 10, but will very work with other providers, such as Linode or Amazon, or on any computer which will run GNU/Linux, such as a Raspberry PI.

## Deployment of the VPS

Once the deployment of the VPS is finalized, a mail is sent to confirm it, which contains the password for the default Debian user.

Keep your system up-to-date before running any commands

‌```sudo update && sudo apt upgrade```

Your server will need to be able to send e-mails so you can get important security alerts. Unless you're planning on setting up your own mail server, you'll need a way to send e-mails from your server. This will be important for system alerts/messages.

You can use any Gmail account. I recommend you create one specific for this server. That way if your server is compromised, the bad-actor won't have any passwords for your primary account. Granted, if you have 2FA/MFA enabled and you use an app password, there isn't much a bad-actor can do with just the app password, but why take the risk?

Install exim4. You will also need openssl and ca-certificates.

‌```sudo apt install exim4 openssl ca-certificates‌```

Configure exim4:

‌```sudo dpkg-reconfigure exim4-config‌```

Make a backup of /etc/exim4/passwd.client:

‌```sudo cp --archive /etc/exim4/passwd.client /etc/exim4/passwd.client-COPY-$(date +"%Y%m%d%H%M%S")‌```

Add a line like this to /etc/exim4/passwd.client

‌```smtp.gmail.com:yourAccount@gmail.com:yourPassword
*.google.com:yourAccount@gmail.com:yourPassword‌‌‌```

**Notes:**

* Replace yourAccount@gmail.com and yourPassword with your details. If you have 2FA/MFA enabled on your Gmail then you'll need to create and use an app password here.
* Always check host smtp.gmail.com for the most up-to-date domains to list.

## Post-deploy




## Credits

[/drduh/Debian-Privacy-Server-Guide](https://github.com/drduh/Debian-Privacy-Server-Guide)

[/imthenachoman/How-To-Secure-A-Linux-Server](https://github.com/imthenachoman/How-To-Secure-A-Linux-Server)