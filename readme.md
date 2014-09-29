# Senary Harbor

Vagrant virtual environment for Senary Framework and Hack language. Includes:

- HHVM 3.3
- Nginx
- Mysql
- Composer
- Git


## Installation

Make sure you have [VirtualBox](https://www.virtualbox.org/) and [Vagrant](http://www.vagrantup.com/) installed.

Add the `senary/harbor` box:

    $ vagrant add box senary/harbor


Clone the harbor repository to a central location, such as `~/harbor`:

    $ git clone https://github.com/senary/harbor ~/to-wherever-you-want

In `settings.yml` add the path to your public/private key. If you do not have one you can run:

    $ ssh-keygen -t rsa -C "your@email.com"

Setup your shared folders.
- `from` is the path to a folder on your host machine
- `to` is the path that the from folder will be mapped to on the guest machine

Setup sites.
- `url` is the server_name value for nginx
- `root` is the path on the guest machine to the app root


## Working w/ Harbor

SSH: *(if you changed the ip in settings.yml, use that value instead)*

    $ ssh vagrant@192.168.22.22

    $ # you can also use the forwarded ports from settings.yml
    $ ssh vagrant@127.0.0.1 -p 2222


MySQL:
- username is `harbor`
- password is `secret` *(same for root user)*
- Either connect to 192.168.22.22 on port 3306 (or different ip from settings.yml)
- Can also connect via localhost at port 33060

Adding sites after box is running, SSH into Harbor and run:

    $ serve url.app /sync/path/to/public

----------------------------------------------------------------------------

### *Big Thanks*

*Code and inspiration for this project was taken from Laravel's [Homestead](https://github.com/laravel/homestead).
Big thanks as well to Chris Fidao and his [Vaprobash](https://github.com/fideloper/vaprobash) project.*
