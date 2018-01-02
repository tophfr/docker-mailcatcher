# mailcatcher docker image

Here is an unofficial Dockerfile for [mailcatcher][mailcatcher].

It is a very small image (~34 MB uncompressed) available on [docker hub][dockerhubpage] based on [Alpine Linux][alpinehubpage] and using the last available release from the official Github repo of [MailHog][mailhog].


## Changelog

- 2018-01-02 Upgrading Alpine Linux from 3.6 to 3.7
- 2017-05-30 Upgrading Alpine Linux from 3.4 to 3.6
- 2016-10-07 Adding ruby-json
- 2016-09-08 Upgrading mailcatcher from 0.6.4 to 0.6.5
- 2016-06-10 Upgrading Alpine Linux from 3.3 to 3.4
- 2016-04-06 Adding libstdc++
- 2016-03-30 Replacing Debian by Alpine Linux
- ...


## Usage

Get it:

    docker pull tophfr/mailcatcher

Run it:

    docker run -d -p 1080:80 --name smtp tophfr/mailcatcher

Link it:

    docker run -d --link smtp -e SMTP_HOST=smtp --name php56 tophfr/php:5.6
    
Then you can send emails from your app and check out the web interface: http://\<your docker host\>:1080/.


If you want to send emails from your host you can map the 25 port:

    docker run -d -p 1080:80 -p 1025:25 --name mail tophfr/mailcatcher

then send yout emails through your docker host on port 1025 (or any port you want)


## Build

Just clone this repo and run:

    docker build -t tophfr/mailcatcher .


  [mailcatcher]: http://mailcatcher.me/ "MailCatcher fake SMTP server with web interface" 
  [dockerhubpage]: https://hub.docker.com/r/tophfr/mailcatcher/ "Mailcatcher docker hub page"
  [alpinehubpage]: https://hub.docker.com/_/alpine/ "A minimal Docker image based on Alpine Linux with a complete package index and only 5 MB in size!"
