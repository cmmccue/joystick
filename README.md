# flystick

A python script for Raspberry Pi that reads a USB joystick
(with [pygame](http://www.pygame.org/)) and outputs a PPM signal to
RC transmitter (with [pigpio](http://abyz.co.uk/rpi/pigpio/python.html)).


The input/output-mapping and visualization are
[highly configurable](flystick_config.py).

## [Demo video](https://www.youtube.com/watch?v=MNFTjIzeuHE)

## Setup (on Raspberry Pi)

### Installation

1. `sudo apt-get install python-pygame git`

2. http://abyz.co.uk/rpi/pigpio/download.html

3. *Optional:* from https://github.com/pimoroni/scroll-phat:

   `curl -sS https://get.pimoroni.com/scrollphat | bash`

4. `git clone https://github.com/jsa/flystick.git`

### Configuration

1. Calibrate joystick, see [`jscal`](http://linux.die.net/man/1/jscal). Also the related `jstest`, `jscal-store`, and
`jscal-restore`.

2. [Configure channel mapping](flystick_config.py).

3. [Configure Pi for safe unplugging](https://www.raspberrypi.org/forums/viewtopic.php?p=119884#p128497).

4. Insert to [`/etc/rc.local`](https://www.raspberrypi.org/documentation/linux/usage/rc-local.md) BEFORE THE LINE `exit 0`:

   ```
   pigpiod
   
   cd ~pi/flystick
   python flystick.py &
   cd -
   ```

### Wiring

1. 5V &rarr; Raspberry Pi

2. Raspberry PPM output &rarr; transmitter trainer port
