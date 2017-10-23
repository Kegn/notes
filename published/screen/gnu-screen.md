# GNU Screen

## Start screen 
>>		screen

 - show help 			--> Ctrl+A+?
 - to exit help press space

## control
- detach from screen  		--> Ctrl+A+d
 - reattach			
>>		screen -r
 - list screens
>>		screen -ls
 - reattach to specific
>>		screen -r <num>
 - when nesting screens
  - switch to next 		--> Ctrl+A+n
  - previous 			--> Ctrl+A+p
  - record with 		--> Ctrl+A+H
  - screenshot			--> Ctrl+A+h
  - log with 
>>		screen -L
  - lock with			--> Ctrl+A+x

## secure
Add password to lock screen

For security reason, you may want to put the password to your screen session. A Password will be asked whenever you want to re-attach the screen. This password is different with Lock Screen mechanism above.

To make your screen password protected, you can edit “$HOME/.screenrc” file. If the file doesn’t exist, you can create it manually. The syntax will be like this.

password crypt_password

To create “crypt_password” above, you can use “mkpasswd” command on Linux. Here’s the command with password “k123“.

k@arx ~ $ mkpasswd k123
l2BIBzvIeQNOs

mkpasswd will generate a hash password as shown above. Once you get the hash password, you can copy it into your “.screenrc” file and save it. So the “.screenrc” file will be like this.

password l2BIBzvIeQNOs

Next time you run screen and detach it, password will be asked when you try to re-attach it

k@arx ~ $ screen -r 5741
Screen password:

Type your password, which is “k123” and the screen will re-attach
Password:
Screen password:

A Password will be asked to you twice. First password is your Linux password, and the second password is the password that you put in your .screenrc file.
