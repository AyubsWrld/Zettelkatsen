- `sudo systemsetup -setremotelogin`
	- Allow in system settings 
- `ssh username@mac-ip-addr`
	- `ipconfig getifaddr en0`
- Allow on receiving device 
- Then optionally run `caffeinate -d`  to make sure the device hosting the session does not turn off.
____
Tags : #Networking #ssh