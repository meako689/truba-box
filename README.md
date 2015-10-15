#Truba box

This is a Vagrant Ubuntu (Trusty 64) box with a single ansible playbook for setting up django development for truba project

## What's included

provisions:

- Nginx
- uWSGI
- Postgresql
- Python
- Virtualenv
- PIL dependencies to support jpg, zlib, freetype
- Git
- Vim
- Sass stuff

## Usage

- clone or put truba project source code into current dir
- `vagrant up`
- `vagrant ssh` to get inside VM
- your project is in `/vagrant` dir inside VM which is automatically synced with this folder
- install requirements, do stuff (virtualenv is created and activated automatically), develop
- get a dump of the database and optionally media files, import them

That's it! You are all set.

Now you can run 
```python manage.py runserver 0.0.0.0:8000```
inside VM and get your project on `192.168.192.168:8000` Also there is nginx+uwsgim, but usually you have to spend some time to set it up properly. (TODO)

## Note

You may want to:

- Run `git config --global` to set your `user.name` and `user.email`
