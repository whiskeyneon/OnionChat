![OnionChat](http://i.imgur.com/lQpoAzL.png)

# [OnionChat](https://chatrapi7fkbzczr.onion)
## [chatrapi7fkbzczr.onion](https://chatrapi7fkbzczr.onion)
Anonymous realtime chat. No JS.

## Deploy

The only external dependency is redis.  Make sure you have it running locally
on port 6379.  You should be able to modify the database using `config.ini`
(which will be generated automatically when you first run the server.)

You must also have libevent-dev installed.

    sudo apt-get install libevent-dev

All other dependencies are in `requirements.txt`.

    pip install -r requirements.txt
    python nodotjs/server.py staging

You can also change which port the server runs on in `config.ini`.

## Built on No.js

[Read](http://blog.accursedware.com/html-only-live-chat:-No.JS/) about it.
