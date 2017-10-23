#systemd-timers

###from https://wiki.gentoo.org/wiki/Systemd#Timer_services


~/.local/share/systemd/user/backup-work.timer    # Example of a timer running every working day

[Unit]
Description=daily backup work
RefuseManualStart=no
RefuseManualStop=no
 
[Timer]
Persistent=false
OnCalendar=Mon-Fri *-*-* 11:30:00
Unit=backup-work.service
 
[Install]
WantedBy=default.target




~/.local/share/systemd/user/backup-work.serviceExample of a service triggering backup

[Unit]
Description=daily backup work
RefuseManualStart=no
RefuseManualStop=yes

[Service]
Type=oneshot
ExecStart=/home/<user>/scripts/backup-work.sh

Replacing cron with systemd timers 


> the following is mostly taken from [[https://wiki.archlinux.org/index.php/Systemd/Timers#Example]]  

Timers are systemd unit files whose name ends in .timer that control .service files or events.

Timers have built-in support for calendar time events, monotonic time events, and can be run asynchronously.

Timers are like other unit configuration files and are loaded from the same paths but include a [Timer] section. The [Timer] section defines when and how the timer activates. Timers are defined as one of two types:

    Monotonic timers activate after a time span relative to a varying starting point. (stop if machine suspended or off)
    Realtime timers (a.k.a. wallclock timers) activate on a calendar event (like cronjobs). The option OnCalendar= is used to define them.

---


### Service units
For each .timer file, a matching .service file exists (e.g. foo.timer and foo.service). The .timer file activates and controls the .service file. The .service does not require an [Install] section as it is the timer units that are enabled. If necessary, it is possible to control a differently-named unit using the Unit= option in the timer's [Timer] section. 

>>     $ systemctl list-timers
>>     $ systemctl list-timers --all

### Monotonic timer

A timer which will start 15 minutes after boot and again every week while the system is running.

/etc/systemd/system/foo.timer

[Unit]
Description=Run foo weekly and on boot

[Timer]
OnBootSec=15min
OnUnitActiveSec=1w 

[Install]
WantedBy=timers.target

Realtime timer

A timer which starts once a week (at 12:00am on Monday). It starts once immediately if it missed the last start time (option Persistent=true), for example due to the system being powered off:

/etc/systemd/system/foo.timer

[Unit]
Description=Run foo weekly

[Timer]
OnCalendar=weekly
Persistent=true     
 
[Install]
WantedBy=timers.target

The format controlling OnCalendar events uses the following format when more specific dates and times are required: DayOfWeek Year-Month-Day Hour:Minute:Second. An asterisk may be used to specify any value and commas may be used to list possible values. Two values separated by .. may be used to indicate a contiguous range.

OnCalendar=Mon,Tue *-*-01..04 12:00:00

 Tip: Special event expressions like daily and weekly refer to specific start times and thus any timers sharing such calendar events will start simultaneously.


 MAILTO

You can set up systemd to send an e-mail when a unit fails. Cron sends mail to MAILTO the job outputs to stdout or stderr, but many jobs are setup to only output on error. First you need two files: an executable for sending the mail and a .service for starting the executable. For this example, the executable is just a shell script using sendmail:

/usr/local/bin/systemd-email

```
#!/bin/bash

/usr/bin/sendmail -t <<ERRMAIL
To: $1
From: systemd <root@$HOSTNAME>
Subject: $2
Content-Transfer-Encoding: 8bit
Content-Type: text/plain; charset=UTF-8

$(systemctl status --full "$2")
ERRMAIL
```

Whatever executable you use, it should probably take at least two arguments as this shell script does: the address to send to and the unit file to get the status of. The .service we create will pass these arguments:

/etc/systemd/system/status-email-user@.service

[Unit]
Description=status email for %i to user

[Service]
Type=oneshot
ExecStart=/usr/local/bin/systemd-email address %i
User=nobody
Group=systemd-journal

Where user is the user being emailed and address is that user's email address. Although the recipient is hard-coded, the unit file to report on is passed as an instance parameter, so this one service can send email for many other units. At this point you can start status-email-user@dbus.service to verify that you can receive the emails.

Then simply edit the service you want emails for and add OnFailure=status-email-user@%n.service to the [Unit] section. %n passes the unit's name to the template.
Note:

    If you set up SSMTP security according to SSMTP#Security the user nobody will not have access to /etc/ssmtp/ssmtp.conf, and the systemctl start status-email-user@dbus.service command will fail. One solution is to use root as the User in the status-email-user@.service unit.
    If you try to use mail -s somelogs address in your email script, mail will fork and systemd will kill the mail process when it sees your script exit. Make the mail non-forking by doing mail -Ssendwait -s somelogs address.
