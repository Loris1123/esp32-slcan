# esp32-slcan

ESP32 firmware, to transform an ESP32 Devkit into a CAN interface for slcan.

Bluetooth and display overhead was removed.
Libraries used from https://github.com/nhatuan84/arduino-esp32-can-demo

Thanks @mintynet and @nhatuan84 for the work!

# Installation

## Software
Use Arduino SDK to upload the project file to the ESP32.

## Hardware
Connect your CAN tranceiver to your ESP32.

 - GPIO4 -> CAN Tranceiver TX
 - GPIO5 -> CAN Tranceiver RX

 Also don't forget GND and 3.3V of course.

# Usage

For sending and recieving packets in a basic manner, the interface can be used with a direct serial connection.
For more complex tasks, the slcan drivers can be used, what makes the interface compatible with many other tools.

## Serial Connection

Use your favorite terminal emulator, such as picocom.

    picocom -b 500000 /dev/ttyUSB0

Then type `h<ENTER>` to view the help text.

## slcan

Install can-utils (https://github.com/linux-can/can-utils)

    sudo slcan_attach -f -s6 -o /dev/ttyUSB0
    sudo slcand -o -c -s6 /dev/ttyUSB0 -S 500000
    sudo ip link set slcan0 up

    # Test if the interface is working
    candump slcan0


