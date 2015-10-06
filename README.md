devenv-scrum-reporting
===============

Early development environment for the scrum reporting tool

## About

This development environment is designed to be easy to use, and function very similarly to a server environment.

Requirements:
 - Vagrant < 1.4
 - Virtualbox < 4.3.20


## TL;DR

Inside the project folder, simply run `vagrant up` and then connect to your projects on the ports defined in `configuration.yaml`

## Useful commands

All the apps are run by supervisord, here are some helpful aliases for supervisorctl.
```
status                - view running status of all apps (via supervisorctl)
stop {name of app}    - stop app running in supervisord
start {name of app}   - start app running in supervisord
restart {name of app} - restart app running in supervisord
reload                - reload supervisord config and restart all apps
startsup              - start supervisord (needed after a vagrant halt/vagrant up)
```
To run the app in the terminal (i.e. not via supervisord, so you can directly see the output)
```
lr-run {name of app}
```

To quickly view the logs of an app
```
lr-log {name of app}
```

## Apps
### [Scrum Report API:](https://github.com/LandRegistry/scrum-reporting-prototype)

`localhost:5001`
- **GET** `/scrum/`

### [Scrum Report Frontend:](https://github.com/LandRegistry/scrum-reporting-prototype)

`localhost:5002`
- **GET** `/scrum/`
- **GET** `/scrum/<team>/<sprint number>`
- **POST** `/scrum/`

## Notes
The development environment relies on [Vagrant](https://www.vagrantup.com/).
Currently only Virtualbox is supported as a provider.

For further information on managing Vagrant you can read the [official documentation](https://docs.vagrantup.com/v2/).

##How to query the postgres database with PSQL

Login to the centos virtual machine.  Switch to root with:

```
sudo -i
```

login to the system of record database with this:

```
psql -U workingregister workingregister
```
