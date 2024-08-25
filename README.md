# Attiny85 programming using PlatformIO

**Table of Content**

1. [Introduction](#introduction)
2. [Programming the Attiny85](#programming-the-attiny85)
3. [Using `RESET` as an IO pin](#using-reset-as-an-io-pin)

## Introduction

This repo is collection of all that is needed to program an Attiny85 using
[PlatformIO].

The Attiny85 is a very capable MCU for small applications. It has 5 usable IO
pins in the standard configuration, but can not easily connected to a USB port
for programming or serial communications.

Furthermore, although it has 6 IO pins, only 5 is available since one is used
as dedicated `RESET` pin needed for programming. There is a way to enable this
pin for general IO, but comes with some caveats, and some ways to circumvent
those caveats, so it become a more complex topic.

If your application requires 6 IOs however, then this repo also contains the
info on tackling this.

## Programming the Attiny85

All the details for this is contained in the [ISP] section if this repo.

It explains how to use an Adruino Nano as programmer for the Attiny85. This
involves uploading a specific programming program to the Nano, connections
between Nano and Attiny85, and the [PlatformIO] setup for uploading to the
Attiny85.

## Using `RESET` as an IO pin

In order to use the `RESET` pin as a GPIO, you need to change a fuse setting on
the MCU. The caveat is that disabling the `RESET` function does not allow it be
programmed using the [ISP] anymore.

The [FuseResetter] setcion of this repo has all the details needed to reset the
fuses so that the `RESET` function is available again, allowing it to be
programmed again.

To reset the fuses, you need a **High Voltage Programmer** which basically
allows programming new fuse settings while a using a high voltage (12V) on the
reset pin of the MCU. This programmer is described in the [FuseResetter]
section, as well as the process for doing the reset.


<!-- Links -->
[PlatformIO]: https://platformio.org/
[ISP]: ./ISP/
[FuseResetter]: ./FuseResetter/
