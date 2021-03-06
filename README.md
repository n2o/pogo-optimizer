# Pokemon GO Optimizer with Docker support

[![Travis CI](https://api.travis-ci.org/n2o/pogo-optimizer.svg?branch=master)](https://travis-ci.org/n2o/pogo-optimizer)

[From the devs](https://github.com/justinleewells/pogo-optimizer): **This project is no longer being developed because as of July 30th Niantic has implemented SSL pinning, rendering this method useless. Happy hunting, everyone.**

This is a fork from the [original project](https://github.com/justinleewells/pogo-optimizer), which enhances the installation experience. 

## Setup with Dockerhub
There is an automated build on Dockerhub: [cmeter/pogo-optimizer](https://hub.docker.com/r/cmeter/pogo-optimizer/)

So you don't need to clone the repository:

```bash
$ docker run -d -p 3000:3000 -p 8081:8081 -it cmeter/pogo-optimizer
```

## Setup using Docker
To install and setup everything using Docker, build the image in the root directory of this repository with:

```bash
$ git clone --recursive https://github.com/n2o/pogo-optimizer.git
$ git submodule foreach git pull origin master
$ docker build -t pogo .
```

Since I included his project as a submodule, the command `git submodule ...`
updates it to the latest version and contains all changes he made in his repository.

Then create a container with the same ports as described above with this command:

```bash
$ docker run -d -p 3000:3000 -p 8081:8081 -it pogo
```

## Original Readme

This tool shows you the IVs and information necessary to determine which Pokemon get ground into candy. Perfect for any trainer aspiring to be the very best.

I have been told that it's a possibility Niantic could get mad at us for using this, but I'll let you know if I hear anything for them. I imagine that it's safe for the time being.

![example](http://i.imgur.com/3V8xw1G.png)

## Host Setup
So, first of all, you need node.js, protobuf, and git (obviously). I've only tested this on Mac, so if you want to test it on other platforms, be my guest.

### Mac OSX

Run these commands:

```
git clone https://github.com/justinleewells/pogo-optimizer
cd pogo-optimizer
brew install --devel protobuf
npm install
bower install
node index
```

### RPM-based Linux (Fedora, CentOS, RHEL)

Run these commands:

```
sudo dnf install nodejs protobuf protobuf-devel
sudo npm install -g bower
git clone https://github.com/justinleewells/pogo-optimizer
cd pogo-optimizer
npm install
bower install
node index
```

Now you should have a webserver running. Make sure your phone and computer are connected to the same wireless network.

## Phone Setup

Next, check your network settings for your internal ip address.
If your host computer's IP is 10.0.1.3, you'll add 10.0.1.3:8081 as a proxy on your phone.

Next, visit http://10.0.1.3:3000/ca.pem and install the certificate.

After accepting the certificate, open Pokemon GO on your phone. After you can see your character walking around, go to localhost:3000 on your host machine. Enjoy.

### Android

To set up a WiFi proxy on your Android 6.0.1+ phone, follow these steps:

* Go to Settings > WiFi.
* Choose your WiFi network from the list.
* Select 'edit'
* Select 'Show advanced options'
* Under "Proxy," change the setting from None to Manual.
* Enter e.g. 10.0.1.3 as the proxy name.
* Enter 8081 as the port

## TODO

* Remove Pokemon after they have been transferred
* Make client usable while catching Pokemon

## Feature Requests/Suggestions

I'd love to hear what feature requests and suggestions you all have, so feel free to shoot me an email.
