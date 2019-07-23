# Rover control
The rover is controlled by a control panel provided by the competition organisiers. The panel has 4 switches, 2 buttons and one potentiometer. Teams can assign their contol functions to these gadgets as they prefer.

The control panel will be connected to MaM-GND hardware, which then sends control packets to the rover, and control+housekeeping information to [UGND](https://github.com/legokor/UniversalGnd) for display.

## Control packet protocol
See [MaM 2019 Message Protocol](https://github.com/legokor/UniversalGnd/wiki/MaM-2019-Message-Protocol) on the UGND Wiki.

## Controls layout
The available control gadgets are assigned control functions as follows:

### Switches
Switch | Function
--- | ---
**Switch 0 (`SW0`)** | Emergency switch. When ***on***, it overrides everything else and spams `STOP` to the rover. When ***off*** it has no effect.
**Switch 1 (`SW1`)** | Mode switch, only has effect when `SW3` is ***off***. When ***on*** it sets control mode to `collect`; when ***off*** it sets control mode to `dump`.
**Switch 2 (`SW2`)** | Cruise speed switch. When ***on***, it sets cruise speed to `high`, when ***off*** it sets the cruise speed to `low`.
**Switch 3 (`SW3`)** | Cruise mode switch. When ***on*** it overrides `SW1` and sets control mode to `cruise`. When ***off*** it has no effect.

### Button 0 (`BT0`)
Function depends on control mode:

Mode | Function
--- | ---
**`cruise`** | When pressed, commands the rover to move forwards with the speed set by `SW2` and turn angle set by `POT`.
**`collect`** | When pressed, commands the rover to tilt the collection arm to the angle set by `POT`. 
**`dump`** | When pressed, commands the rover to tilt the dumper to the angle set by `POT`.

When released, the rover gets sent a `STOP` packet.

### Button 1 (`BT1`)
Function depends on control mode:

Mode | Function
--- | ---
**`cruise`** | When pressed, commands the rover to move backwards with the speed set by `SW2` and turn angle set by `POT`. When released, the rover gets sent a `STOP` packet.
**`collect`** | No effect.
**`dump`** | No effect.

### Potentiometer (`POT`)
Function depends on control mode:

Mode | Function
--- | ---
**`cruise`** | Specifies rover turn angle.
**`collect`** | Specifies collection arm tilt angle.
**`dump`** | Specifies dumper angle.
