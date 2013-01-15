```
.-..-..---..---..---..---..---. .---..---..---. 
| || || |-' \ \ `| |'| | || |-< `| |'| |- | |-< 
`----'`-'  `---' `-' `-^-'`-'`-' `-' `---'`-'`-'
```
## What
An [upstart](http://upstart.ubuntu.com/) script that runs the scripts in each user's ~/init folder on net-device-up.

## Why
Allows a non-privileged user to 'install' services that will run at boot.

## How
Users place start scripts for the services they would like to run at boot in ~/init. When the net-device-up event occurs, upstarter loops over each user in /etc/passwd and executes the contents of their ~/init directories via `sudo -u`.

## Install
You'll need to be root:  
`curl -o /etc/init/upstarter.conf https://raw.github.com/jessetane/upstarter/master/upstarter.conf`

## Notes
Note that running a script with `sudo -u` does NOT guarantee the script's environment will look the same as when owner has an interactive login! Ensuring a properly configured environment is the responsibility of a service's start script.

## License
MIT
