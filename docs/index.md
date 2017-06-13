# Connecting a New Device

Follow the instructions below to connect your device to the [Cloud4RPI](https://cloud4rpi.io) control panel.

## Prerequisites

It is advisable to update your system before installing.

``` bash
$ sudo apt-get update && sudo apt-get upgrade
```

Install/update the required packages.

``` bash
$ sudo apt-get install wget unzip python python-pip
```

You can use alternative methods to [install pip](https://pip.pypa.io/en/stable/installing.html).

!!! Note
    The Cloud4rpi library is compatible with Python 2.7.9+ and Python 3.2+ versions.


### [Optional] Enable interfaces
If your OS is [Raspbian](https://www.raspberrypi.org/downloads/raspbian/), follow the steps below:

- Run `sudo raspi-config`
- Open a section for configuring additional interfaces (`Advanced Options` or `Interfacing Options | Configure connections to peripherals` depending on the version).
- Enable I2C, 1-wire and other necessary interfaces.
- Choose `<Finish>`.
- Reboot the device with the `sudo reboot` command.


## Getting the Cloud4RPI Client Library

Install the library using your preferred Python version. The following command installs and integrates Cloud4RPI with your OS's default Python interpreter (usually Python 2):

``` bash
$ sudo pip install cloud4rpi
```

If you are using Python 3, use the following command:

``` bash
sudo python3 -m pip install cloud4rpi
```

!!! Note
    For information on how to work with several versions of Python installed, see [Python Documentation](https://docs.python.org/3/installing/).

## Hacking Together some Code

We have prepared several samples in the [examples](https://github.com/cloud4rpi/cloud4rpi-examples) repository to demonstrate sending data to the Cloud.

Get the **cloud4rpi-examples-master** directory on your device.

``` bash
wget https://github.com/cloud4rpi/cloud4rpi-examples/archive/master.zip && unzip master.zip && rm master.zip
```

Before running a sample, remember to insert your device token to the line like this:

``` python
DEVICE_TOKEN = '__YOUR_DEVICE_TOKEN__'
```

Use a text editor (for instance, `nano`) to replace `__YOUR_DEVICE_TOKEN__` with the token displayed at the top of the device page. If it does not display anything on the [Devices](https://cloud4rpi.io/devices) page, you can create a device using the **New Device** button in the top right corner, and use its token.


## Running

Execute the script with the Python interpreter, for example:

``` bash
$ sudo python minimal.py
```

!!! Note
    If you have installed Cloud4RPI to a non-default Python, use the version with the Cloud4RPI library.

If the script output looks right, open the [Devices](https://cloud4rpi.io/devices) page to see if the device status has changed.


## Installing as a service

You can use our service templates to facilitate service installation. Pass the path to your Cloud4RPI-enabled Python script to the [service_install.sh](https://github.com/cloud4rpi/cloud4rpi/blob/master/service_install.sh) script as a parameter.

You can use the piped script technique to do this in a single line.

``` bash
wget -O - https://raw.githubusercontent.com/cloud4rpi/cloud4rpi/master/service_install.sh | sudo bash -s your_script.py
```

If you are not comfortable running a piped script, or if your Internet connection is unstable, download and run the script manually.

``` bash
wget https://raw.githubusercontent.com/cloud4rpi/cloud4rpi/master/service_install.sh
chmod +x service_install.sh
sudo ./service_install.sh your_script.py
```

!!! Note
    You need to replace 'your_script.py' with the actual path to your service script.