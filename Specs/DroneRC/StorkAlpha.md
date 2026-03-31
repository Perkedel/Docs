# Stork `A` (Alpha)

Lightweight tough plastic drones. A pre-built flagship, where pre-designed case, batteries, and modules always ship as one. It's designed to be usable out-of-the box.

`A` is also very cheap and affordable, but still has the same guts as the other DIY drones.

The casing and batteries are pre-designed, to achieve best compact and lightweight design.

Inspired from DJI Neo series. But unlike those brands, `A` drone can be used immediately without login (using ELRS compatible Antenna) and be flown over 120 m. You are responsible to pay those fine and be arrested.

## Points

- Battery on bottom. Acts as weight, so center of gravity is lower
- Components on top.
- Using same Corazon PCBs. Put side by side, front back. All are heatsank. Front to back
  - Aorta. this PCB card binds to the camera skeleton instead.
  - MCU
  - ESC
- Heatsink plate on the top also houses the orientative sensors & Antennas
- Battery is in-house design like DJI's. So it has a power combo button, & BMS. Unfortunately these are soldered coz that's the most reliable design. 
  - Press once to check juice left
  - Press once then press hold to Power switch. 
    - In OFF, it turns on the drone, 
    - and in ON, sends shutdown command. 
    - attempting Power-ON command in charging cradle wakes up the cradle if not ON already, and wake all other batteries to tell juice left.
    - Cradle can reverse charge to other device if USB mode asked is powerbank mode

## Camera type

`A` drone camera is interchangable

- 360 camera. Switchable 360 degree camera.
- Pocket camera. Gimbal-axis camera. Supports Pitch, Roll, & Yaw. The sensor is also square 1:1, allowing various kinds of resolution both landscape, portrait, or as is.