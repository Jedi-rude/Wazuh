# Email Alerts Configurations
Wazuh can be configured to send email alerts to one or more email addresses when certain rules are triggered or for daily event reports. 

## Pre-requisite
- SMTP server 
- Wazuh SIEM
- Email address & app passwords

## SMTP server configuration
This SMTP server configuration can be varied on different distrobution, this lab will configure postfix mail service(SMTP) with ubuntu os.
Firstly, run following commands to install postfix & certificates modules.
- ``` apt-get update && apt-get install postfix mailutils libsasl2-2 ca-certificates libsasl2-modules ```

After installation is complete, configure postfix server configurations files are located at ``` /etc/postfix/main.cf ```. And put following configurations.
```
relayhost = [smtp.gmail.com]:587
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options = noanonymous
smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt
smtp_use_tls = yes
smtpd_relay_restrictions = permit_mynetworks, permit_sasl_authenticated, defer_unauth_destination
```
<p align="center"><img src="https://github.com/AungZayMyo/Wazuh/assets/154745254/7241f647-893f-4b04-a919-cfe3186b0cd6" width="400px" height="250px"><br>Figure (1) postfix configurations</p>

After that run following commands step by step.
```
echo [smtp.gmail.com]:587 USERNAME@gmail.com:PASSWORD > /etc/postfix/sasl_passwd
postmap /etc/postfix/sasl_passwd
chmod 400 /etc/postfix/sasl_passwd
```
Which username is your email address. 
Which password is your gmail app password somethings like following figure.
<p align="center"><img src="https://github.com/AungZayMyo/Wazuh/assets/154745254/aa559f84-6f91-4284-be82-b540d5c6d3ee" width="400px" height="250px"><br>Figure (2) </p>

After that restart email service ``` systemctl restart postfix ```. And test email using following commands.
- ``` echo "Test mail from postfix" | mail -s "Test Postfix" -r "you@example.com" you@example.com ```
It will sends somethings like following figure.

<p align="center"><img src="https://github.com/AungZayMyo/Wazuh/assets/154745254/daa6a9ae-a596-47d8-ab22-103b1df925cd" width="500px" height="250px"><br>Figure (3) </p>
SMTP server configuration is done.

## Wazuh email alerts configuration
In order to configure Wazuh to send email alerts, the email settings must be configured in the <global> section of the ossec.conf file which located at ``` /var/ossec/etc/ossec.conf ```. After that configured file as followings.

``` 
<global>
    <jsonout_output>yes</jsonout_output>
    <alerts_log>yes</alerts_log>
    <logall>no</logall>
    <logall_json>no</logall_json>
    <email_notification>yes</email_notification>
    <smtp_server>localhost</smtp_server>
    <email_from>sender@gmail.com</email_from>
    <email_to>receiver@gmail.com</email_to>
    <email_maxperhour>12</email_maxperhour>
    <email_log_source>alerts.log</email_log_source>
    <agents_disconnection_time>10m</agents_disconnection_time>
    <agents_disconnection_alert_time>0</agents_disconnection_alert_time>
  </global>

  <alerts>
    <log_alert_level>3</log_alert_level>
    <email_alert_level>7</email_alert_level>
  </alerts>
<global>
```
After that restart wazuh manager ``` systemctl restart wazuh-manager ```. I will delete some files from file integrity monitoring folder.
<p align="center"><img src="https://github.com/AungZayMyo/Wazuh/assets/154745254/5f607192-864a-4857-950c-e129dd274d8f" width="500px" height="250px"><br>Figure (4) alerts </p>

When alerts level reached 7 or above wazuh will sends emails to you like followings figures.
<p align="center"><img src="https://github.com/AungZayMyo/Wazuh/assets/154745254/df83eddd-7d31-4416-9aaa-f17aa0438fa4" width="500px" height="250px"><br>Figure (5) Wazuh Email Alerts</p>
<p align="center"><img src="https://github.com/AungZayMyo/Wazuh/assets/154745254/b19ef456-257c-442a-bd3b-16579587fd14" width="500px" height="300px"><br>Figure (6) Wazuh Email Alerts</p>

## Conclusion

In this tutorial, Wazuh Email Alerts Configurations & SMTP server Configurations is demostrated. Do more Practice and Expert it!. <br>
**4/1/2024** <br>
Contributed By - Jord@n
