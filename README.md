# esp32-slcan

ESP32 firmware, to transform an ESP32 Devkit into a CAN interface for slcan.

Fork of https://github.com/Loris1123/esp32-slcan.
Thanks @mintynet for the work!
Bluetooth and display overhead was removed.

# Requirements
Requires the use of the Arduino library https://github.com/nhatuan84/arduino-esp32-can-demo

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


