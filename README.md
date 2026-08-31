![Scroll pHAT HD](scroll-phat-hd-logo.png)
https://shop.pimoroni.com/products/scroll-phat-hd

https://shop.pimoroni.com/products/scroll-hat-mini

17x7 pixels of single-colour, brightness-controlled, message scrolling goodness! This library will work with Scroll pHAT HD and Scroll HAT Mini.

## Installing

### Full install (recommended):

We've created an easy installation script that will install all pre-requisites and get your Scroll pHAT HD
up and running with minimal efforts. To run it, fire up Terminal which you'll find in Menu -> Accessories -> Terminal
on your Raspberry Pi desktop, as illustrated below:

![Finding the terminal](http://get.pimoroni.com/resources/github-repo-terminal.png)

In the new terminal window type the command exactly as it appears below (check for typos) and follow the on-screen instructions:

```bash
curl https://get.pimoroni.com/scrollphathd | bash
```

Alternatively, on Raspbian, you can download the `pimoroni-dashboard` and install your product by browsing to the relevant entry:

```bash
sudo apt-get install pimoroni
```
(you will find the Dashboard under 'Accessories' too, in the Pi menu - or just run `pimoroni-dashboard` at the command line)

If you choose to download examples you'll find them in `/home/pi/Pimoroni/scrollphathd/`.

### Manual install:

#### Library install for Python 3:

on Raspbian:

```bash
sudo apt-get install python3-scrollphathd
```

other environments: 

```bash
pip3 install scrollphathd
```

This library requires Python 3.7 or newer and is tested up to Python 3.14.

#### Install from this repository:

The installable package lives in the `library/` subdirectory of this repository,
so any install straight from GitHub must point at it with `subdirectory=library`.

To add it as a dependency of another [uv](https://docs.astral.sh/uv/) project:

```bash
uv add "scrollphathd @ git+https://github.com/JensPfeifle/scroll-phat-hd.git#subdirectory=library"
```

To pull in the optional Flask-based HTTP API dependencies as well, request the
`http` extra:

```bash
uv add "scrollphathd[http] @ git+https://github.com/JensPfeifle/scroll-phat-hd.git#subdirectory=library"
```

For a one-off install into the current environment:

```bash
uv pip install "git+https://github.com/JensPfeifle/scroll-phat-hd.git#subdirectory=library"
```

Append `@<branch>`, `@<tag>` or `@<commit>` after `.git` to pin a specific
revision, e.g. `...scroll-phat-hd.git@master#subdirectory=library`. `numpy` and
`smbus2` are installed automatically as dependencies. The same URLs work with
plain `pip` in place of `uv pip`.

##### Installing on an older Raspberry Pi OS (e.g. Buster, 32-bit):

On 32-bit Raspberry Pi OS there are no prebuilt `numpy` wheels on PyPI, so a
plain install tries to compile `numpy` from source and usually fails. Use the
[piwheels](https://www.piwheels.org/) index, which serves prebuilt ARM wheels,
and install against the system Python so the wheel tags match:

```bash
uv add --python "$(command -v python3)" \
  --index https://www.piwheels.org/simple \
  "scrollphathd @ git+https://github.com/JensPfeifle/scroll-phat-hd.git#subdirectory=library"
```

The `--index` flag adds piwheels ahead of PyPI while still falling back to PyPI
for anything piwheels doesn't carry, so `numpy` installs as a prebuilt wheel
with no compilation. If you prefer plain `pip`, piwheels is already configured
in `/etc/pip.conf` on Raspberry Pi OS, so `pip3 install "git+...#subdirectory=library"`
works too. Note that Buster is end-of-life; upgrading to Bullseye or Bookworm is
recommended where possible.

### Development:

This project is managed with [uv](https://docs.astral.sh/uv/) and uses a
standard `pyproject.toml`. If you want to contribute, or like living on the
edge of your seat by having the latest code, clone this repository, `cd` to
the `library` directory, and run:

```bash
uv sync
```

To include the optional Flask-based HTTP API dependencies, run:

```bash
uv sync --extra http
```

You can then run commands inside the managed environment with `uv run`, e.g.:

```bash
uv run python examples/hello-world.py
```

In all cases you will have to enable the i2c bus.

## Alternative Libraries

* Node JS library by @whatsim - https://github.com/whatsim/scrollcontroller

## Documentation & Support

* Guides and tutorials - https://learn.pimoroni.com/scroll-phat-hd
* Function reference - http://docs.pimoroni.com/scrollphathd/
* GPIO Pinout - https://pinout.xyz/pinout/scroll_phat_hd
* Get help - http://forums.pimoroni.com/c/support

## Unofficial / Third-party libraries

* Java library by Jim Darby - https://github.com/hackerjimbo/PiJava
* Rust library by Tiziano Santoro - https://github.com/tiziano88/scroll-phat-hd-rs
* Go library by Tom Mitchell - https://github.com/tomnz/scroll-phat-hd-go
