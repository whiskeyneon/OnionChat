![OnionChat](http://i.imgur.com/lQpoAzL.png)

# [OnionChat](https://chatrapi7fkbzczr.onion)
## [chatrapi7fkbzczr.onion](https://chatrapi7fkbzczr.onion)
Anonymous realtime chat. No JS.

## Development

The only external dependency is redis.  Make sure you have it running locally
on port 6379.  You should be able to modify the database using `config.ini`
(which will be generated automatically when you first run the server.)

You must also have libevent-dev installed.

    sudo apt-get install libevent-dev

All other dependencies are in `requirements.txt`.

    pip install -r requirements.txt
    python nodotjs/server.py staging

You can also change which port the server runs on in `config.ini`.

## Deployment

OnionChat uses Brubek as a server, so there's no need to proxy, but you'll probably want to use it as an upstart service. Add 'onionchat.conf' to your /etc/init/:

    description "OnionChat"
     
    start on runlevel [2345]
    stop on runlevel [016]
     
    respawn
    exec /home/www/OnionChat/env/bin/python /home/www/OnionChat/nodotjs/server.py production /home/www/OnionChat/config.ini >> /var/log/onionchat.log 2>&1

(Assuimg you have a deploy user with a 'www' home folder). You'll also have to make sure that your config.ini includes an absolute path to your templates directory.

### Configuring your hidden service.

You'll probably want to consult the [tor hidden services deploy guide](https://www.torproject.org/docs/tor-hidden-service) to set this up. 

Then, in your /etc/tor/torrc:

    HiddenServiceDir /var/lib/tor/hidden_service/
    HiddenServicePort 80 127.0.0.1:7000

And set up your keys and hostname in /var/lib/tor/hidden_service/
.

### Hardening

Make sure that your server doesn't serve 7000 to the outside world!

## Built on No.js

[Read](http://blog.accursedware.com/html-only-live-chat:-No.JS/) about it.
