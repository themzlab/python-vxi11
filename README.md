# Python VXI-11 Readme

This is for my own use, forked from here:
http://alexforencich.com/wiki/en/python-vxi11/start

GitHub repository of this fork:

https://github.com/themzlab/python-vxi11/tree/raiseerrors

GitHub repository of original project:
https://github.com/python-ivi/python-vxi11

Google group:
https://groups.google.com/d/forum/python-ivi



## Why the fork

- work on raising errors from socket timeouts to keep my app from crashing

- linting using PyCharm and pylint

- Python 3.9+ and not worry to retain compatibility with older Python versions

  

## Introduction

Python VXI-11 provides a pure Python VXI-11 driver for controlling instruments
over Ethernet.

## Requirements

* Python 3.9

## Installation

activate virtual environment as desired and/or make sure to use the specific python interpreter for which you want this module

    python -m pip install git+ssh://git@github.com/themzlab/python-vxi11.git

## Usage examples

Connecting to Agilent MSO7104A via LXI:

    import vxi11
    instr =  vxi11.Instrument("192.168.1.104")
    print(instr.ask("*IDN?"))
    # returns 'AGILENT TECHNOLOGIES,MSO7104A,MY********,06.16.0001'

Connecting to Agilent E3649A on GPIB address 5 via HP 2050A GPIB bridge:

    import vxi11
    instr = vxi11.Instrument("192.168.1.105", "gpib,5")
    print(instr.ask("*IDN?"))
    # returns 'Agilent Technologies,E3649A,0,1.4-5.0-1.0'

Connecting to Agilent MSO-X 3014A via USBTMC via Agilent E5810 GPIB bridge:

    import vxi11
    instr = vxi11.Instrument("192.168.1.201", "usb0[2391::6056::MY********::0]")
    print(instr.ask("*IDN?"))
    # returns 'AGILENT TECHNOLOGIES,MSO-X 3014A,MY********,02.35.2013061800'

It is also possible to connect with VISA resource strings like so:

    import vxi11
    instr =  vxi11.Instrument("TCPIP::192.168.1.104::INSTR")
    print(instr.ask("*IDN?"))
    # returns 'AGILENT TECHNOLOGIES,MSO7104A,MY********,06.16.0001'

and:

    import vxi11
    instr = vxi11.Instrument("TCPIP::192.168.1.105::gpib,5::INSTR")
    print(instr.ask("*IDN?"))
    # returns 'Agilent Technologies,E3649A,0,1.4-5.0-1.0'

and:

    import vxi11
    instr = vxi11.Instrument("TCPIP::192.168.1.201::usb0[2391::6056::MY********::0]::INSTR")
    print(instr.ask("*IDN?"))
    # returns 'AGILENT TECHNOLOGIES,MSO-X 3014A,MY********,02.35.2013061800'

