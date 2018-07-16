---
layout: post
title:  "First Steps"
date:   2018-07-15 19:49:47 +0200
categories: cimon update
---

# Let's get it started
As a first step, I printed the CIMON Design from Thingiverse with a scaling of 50% for all axes.

# Raspberry
Then I took a Raspberry Pi 3 and added a 3.5" GPIO Touch Display to it.

# Installation Steps
In very short, this is what I did so far:
- install latest raspbian
- enable ssh -> in boot Partition: touch ssh
{% highlight ruby %}
sudo raspi-config
sudo apt-get update
sudo apt-get upgrade
{% endhighlight %}

For my display, followed: [https://github.com/goodtft/LCD-show](https://github.com/goodtft/LCD-show)
{% highlight ruby %}
sudo rm -rf LCD-show
git clone https://github.com/goodtft/LCD-show.git
chmod -R 755 LCD-show
cd LCD-show/
sudo ./LCD35-show
{% endhighlight %}

Touch Rotation:
{% highlight ruby %}
sudo nano /etc/X11/xorg.conf.d/99-calibration.conf
add: Option "TransformationMatrix" "0 -1 1 1 0 0 0 0 1"
{% endhighlight %}

Calibrate Touch...
	[https://github.com/notro/fbtft/issues/445](https://github.com/notro/fbtft/issues/445)

Install Virtual Keyboard:
	[http://ozzmaker.com/virtual-keyboard-for-the-raspberry-pi/](http://ozzmaker.com/virtual-keyboard-for-the-raspberry-pi/)

{% highlight ruby %}
sudo apt-get install libfakekey-dev libpng-dev libxft-dev autoconf libtool -y
git clone https://github.com/mwilliams03/matchbox-keyboard.git
cd matchbox-keyboard
./autogen.sh
make
sudo make install
sudo apt-get install libmatchbox1 -y
{% endhighlight %}

First Picture of my CIMON@home:

![image-title-here](/cimonathome/assets/IMG_4700.JPG){:class="img-responsive"}
