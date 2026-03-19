# Stork Corazon core

Corazon (spanish of *heart*) is the drone core unit.

## in General

- Various ESC models. Corazon has multiple types of ESC included or suppliable separately which prefered by either kinds of FPV pilots
  - 8 Bit. uses 8bit ESC that would've been BLHeli_S. This one is pre-installed BLuejay
  - 32 Bit. uses 32bit ESC that would've been BLHeli_32. This one is pre-installed AM32
- Various MCU models. Corazon also has multiple MCU architectures you can select
  - STM32 based (H7 so on)
  - RaspberryPi Micropython (RP2502 etc.)
  - etc., that is the architecture is designed for embedded. Embedded means, that it can start instantly or as long as 1 second from cold boot.
- Does not brick because you used criminals. Our MCU won't brick if you used DJI's VTX, coz let's be honest, reliable VTX is haaaaaaaaard, and chances are, you already have been locked in with your DJI's ecosystem (pls get out if you can), or the air you breathe only embraces DJI for some reason. Thanks to our ever modularity principle, you can replace its VTX module with DJI's one.

## Series

### Hypertrophy

> [!NOTE]  
> Alike of ESC + DJI O5 Pro

Thicc all in one package. The fly unit, 4 ESCs, and VTX combined, but still modular.

It's Hyperthrophy as in heart organ muscle thickens and getting stronger like those fantastical muscular bodybuilders.

### Kepal

> [!NOTE]
> Alike of DJI O5 lite

PCB only units. Consists only of the Fly Unit & VTX. Each module are only separated. you must supply all 4 ESCs yourself. But unlike competitors like DJI, the VTX has MicroSD card slots like Hypertrophy. 

It's Kepal as in heart organ a size of a fist of hand.

### Very modular

Like all Van Elektronische electronics, Corazon is very modular no matter what trim it goes for. Each one got their own name too

- Aorta. VTX. Camera Video module. It is named after this biggest Port side pipe of a 🫀 organ because this is the topmost part, where blood leads to one of the ways, which relatively close to top is Cranial (head), and hence Eyes.
  - 3Cospid. Inspired from 🫀's tricuspid. This is one of the Digital VTX model.
- Serambi (`Atrium` in ID). MCU. Main module / Flight Controller. Considerably the center part of 🫀, where it all began. Blood goes back to the heart.
- Ventrikel. ESCs. Motor drivers. Particularly inspired after the Port side Ventricle (a.k.a. Left Ventricle), which has biggest muscle since to pump blood to whole body, and hence needs largest amount of energy. Corelates to motor driving, with a philosophy be like *driving motors as strong as port ventricles* (lmao Chinese-style philosophy). To hope that this module can drive motors strong & very reliably.