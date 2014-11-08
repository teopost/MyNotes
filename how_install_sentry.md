How install Sentry
===
Visit www.getsentry.com

Create Debian 7.1 64 bit VM

    # Connect to host with SSH
    sh [host] -l root


    # Install sudo (only for debian)
    apt-get install sudo
    
    
    # add non-root user
    adduser sentry


    # add to sudoers
    adduser sentry sudo


    # log as sentry
    su - sentry


    # update the local package index
    sudo apt-get update


    # actually upgrade all packages that can be upgraded
    sudo apt-get dist-upgrade

    # remove any packages that are no longer needed
    sudo apt-get autoremove


    # reboot the machine, which is only necessary for some updates
    sudo reboot

# Comment non-us
vi /etc/apt/sources.list
#deb http://non-us.debian....

    # install python-dev (ask Y to Restart the services question)
    sudo apt-get install build-essential python-dev python-setuptools

    # install distribute
    easy_install distribute

    # use distribute to install pip
    sudo easy_install pip

    # install virtualenv and virtualenvwrapper
    sudo pip install virtualenv virtualenvwrapper

    # to enable virtualenvwrapper add this line to the end of the .bashrc file
    echo "" >> .bashrc
    echo "source /usr/local/bin/virtualenvwrapper.sh" >> .bashrc

    # exit and log back in to restart your shell
    exit
    su - sentry

    # make virtualenv
    mkvirtualenv sentry_env

    # install sentry
    pip install sentry

    # create settings file (file will be located in ~/.sentry/sentry.conf.py)
    sentry init

    # install postgres
    sudo apt-get install postgresql postgresql-contrib libpq-dev

    # install postgres adminpack
    sudo -u postgres psql
    CREATE EXTENSION "adminpack";
    \q

    # change postgres password & create database (change changeme with pasword)
    sudo passwd postgres
    sudo su - postgres
    psql -d template1 -c "ALTER USER postgres WITH PASSWORD 'changeme';"
    createdb sentry
    createuser sentry --pwprompt
    psql -d template1 -U postgres
    GRANT ALL PRIVILEGES ON DATABASE sentry to sentry;
    \q
    exit

    # update config file to use postgres & host (with vim or your editor of choice)
    vi .sentry/sentry.conf.py
    
    # The following are the contents of my sentry.conf.py file
    DATABASES = {
         'default': {
             'ENGINE': 'django.db.backends.postgresql_psycopg2',
             'NAME': 'sentry',
             'USER': 'sentry',
             'PASSWORD': 'sentry',
             'HOST': 'localhost',
             'OPTIONS': {
                 'autocommit': True,
             }
         }
    }

    You will also want to configure your SMTP mail account. I just used my gmail account.

    # going to need psycopg2
    workon sentry_env
    pip install psycopg2

    # set up databse
    sentry upgrade

    # let's try it out! (browser and control-c to break)
    sentry start

    # install nginx
    sudo apt-get install nginx

    # remove the default symbolic link
    sudo rm /etc/nginx/sites-enabled/default

    # create a new blank config, and make a symlink to it
    sudo touch /etc/nginx/sites-available/sentry
    cd /etc/nginx/sites-enabled
    sudo ln -s ../sites-available/sentry

    # edit the nginx configuration file
    sudo vi /etc/nginx/sites-available/sentry
    Here are the contents of my nginx file:

    server {
        # listen on port 80
        listen 80;
    
        # for requests to these domains
        server_name yourdomain.com www.yourdomain.com;
    
        # keep logs in these files
        access_log /var/log/nginx/sentry.access.log;
        error_log /var/log/nginx/sentry.error.log;
    
        # You need this to allow users to upload large files
        # See http://wiki.nginx.org/HttpCoreModule#client_max_body_size
        # I'm not sure where it goes, so I put it in twice. It works.
        client_max_body_size 0;

        location / {
            proxy_pass http://localhost:9000;
            proxy_redirect off;
    
            proxy_read_timeout 5m;
    
            # make sure these HTTP headers are set properly
            proxy_set_header Host            $host;
            proxy_set_header X-Real-IP       $remote_addr;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        }
    }

    That’s about it.

    # restart nginx
    sudo service nginx restart
    
    I’m not really sure of the proper way to keep sentry going. But I just run:

    sentry start &

    Perhaps someone more knowledgable can leave a comment and suggest the
    best way to start the service automatically on reboot.


If somebody want to create an admin account using command line use the following command:

    sentry --config=.sentry/sentry.conf.py createsuperuser
    sentry --config=.sentry/sentry.conf.py repair --owner=<some_username>

Update
---
I set up supervisor as recommend in the comments and the docs to keep sentry runny (though it has never crashed, it does make restarting easier)

    sudo apt-get install supervisor
    sudo vi /etc/supervisor/conf.d/sentry.conf

Add the following to the sentry.conf file:

    [program:sentry-web]
    directory=/home/sentry/
    command=/home/sentry/.virtualenvs/sentry_env/bin/sentry start http
    autostart=true
    autorestart=true
    redirect_stderr=true
    
    # Restart supervisord

    sudo killall supervisord
    sudo supervisord

Upgrading Sentry
---
    workon sentry_env
    pip install sentry --upgrade
    sentry upgrade
    sudo supervisorctl restart sentry-web
    
Reference
---
http://dustindavis.me/setting-up-your-own-sentry-server.html
