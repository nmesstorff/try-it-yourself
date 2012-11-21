# How to setup a minimal system?

![concept yadtshell and yadtclient](https://github.com/downloads/yadt/yadtshell/yadtshell_to_yadtclient.png)

We want to have a minimal setup of YADT, on a single host with dummy services to play with.

## Test-System
You might want to test YADT on a vm. All you need is a red hat based system.

### Prerequisites
* red hat system version 6.x is preferred.
* python >= 2.6.
* yum, rpm and a user with sufficient rights to install/remove packages via `sudo yum`.
* All hosts to be controlled are accessible passwordless via ssh.
* EPEL has to be installed
* passwordless ssh (to localhost)

## Checkout the files
To clone the getting-started repository you will need a git client.

```bash
sudo yum install git
```

Clone the getting-started repository:

```bash
git clone https://github.com/yadt/getting-started
```

## Installation

### Password-less ssh on local machine
```bash
# keep the .ssh path but set the passphrase as you like
ssh-keygen
# copy the id_rsa.pub key to the authorized_key file in your .ssh folder (home directory)
cat .ssh/id_rsa.pub >> .ssh/authorized_key
```

### Execute setup scripts

Then call `./setup.sh` in each of these folders.
The `yum` installation run will then ask you how to proceed: review the actions yum will take
and type `yes` when appropriate.

```bash
sudo mkdir /var/log/yadtshell
sudo chmod 777 /var/log/yadtshell
```

## "Hello World"
Within the `yadtshell` folder, run `./helloworld.sh`.
This script will

1. create a simple target definition file in a new subfolder adequately named "helloworld",
2. define the local host as member of the new target (using its [fqdn](http://en.wikipedia.org/wiki/Fully_qualified_domain_name)), 
3. try to fetch the current status of the target via `yadtshell status` (for more information, see
https://github.com/yadt/yadtshell/wiki/Status-Information and the other [docs](https://github.com/yadt/yadtshell/wiki)).

![yadtshell status](https://github.com/downloads/yadt/yadtshell/yadtshell_status.png)

check out the [yadt cheat sheet](https://github.com/yadt/cheatsheet/downloads)

## Next Steps
Within the yadtshell folder, run `./nextsteps.sh`.
This script will show how to stop and start all services in the helloworld target.
For more commands, see the [wiki](https://github.com/yadt/yadtshell/wiki).

## Deinstallation
To remove all yadt related rpms, run `./cleanup.sh` in both the yadtclient and yadtshell folder.