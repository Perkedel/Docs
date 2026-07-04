# Compare Van Elektronische vs. Racetrack

Compare the two Needles & RC Surface manufacturers!

## Compare!

| Aspect | Van Elektronische / Stork | Racetrack |
| - | - | - |
| Power Type | EV Only | ICE (with Idling Stop a.k.a. Mild Hybrid for some reason), Tandem (Hybrid legit, Genset mode only supported), EV (only in select Realms including all DNB) |
| Transmission | matic only | H shifter minimum 6 speed manual with Insane Torque (`C` Crawl) speed, no matic option, even the EV version |
| Clutch | Always connected | Single, the multi-clutch is currently too experimental |
| Motoring | Each Motor a wheel (4WD independent) | One motor to all wheels with adjustable ratio (4WD), even the EV version |
| Steering Connections | Electronics + Mechanical Binding Switchable, with Power Steering | Mechanical only, with Power Steering |
| Stock Arrangements | Standard with mirroring per steer position | Standard with mirroring per steer position |
| Swapable Bed Batteries | Yes | Yes |
| Blackbox Logger (Dashcam) | Forward & Backward, and in-cabin CCTVs, Memory storage in backmost | Forward & Backward, and in-cabin CCTVs, Memory storage in backmost |
| Infotainment independent off the car | Yes, debugger still available | Yes, debugger still available |
| Cruise Control | Yes, with smart aware | Yes, with smart aware |
| Self Driving | Yes | Yes |
| "I can't drive manual" Matic emulator | - | Yes |
| Lazy Acceleration (On-gear release clutch / brake) | Yes | Yes |
| Charging Port | Yes, on each sides | Yes, even on Hybrid |
| OBD | 2 of them. One is loose port & another is internal for Infotainment | 2 of them. One is loose port & another is internal for Infotainment |

## Background

Van Elektronische always think forward & efficiency. They always make cars that is easy to drive and simple to use. But then, some community in the car scene think that removing the so-called complexity equals to removing the fun of driving. After lengthy times of debate, the community resigned from Van Elektrnische and established Racetrack.

Thankfully, due to DNB's policy in the State Owned Companies, There shall no be competition coming out of government. That, is considered civil war and is not welcome. As the result, Racetrack then must be still owned by Van Elektronische, and to this day they build card each for different demands of the people.  
You see, DNB had a rule that their own state owned business cannot divide. Even tho if weren't, it's Van Elektronische's that'd disagree with break-ups. So until Jesus comes back, Racetrack always belongs to Van Elektronische. And if they resign again to really separate, that's betrayal.

With Racetrack, you can now have everything Van Elektronische think is legacy & backward regression, such as ICE, Hybrids, and even Manual Transmission. All these that those people would define as Fun of Driving, even for centuries.

### Internal Combustion Engines

For centuries, ICE is considered the bane of the nature. It's explosive sounds and the smoke it emits, reeks polution and diseases. So many manufacturers who targets people en masse would move on to EV if there's nothing that inhibits this route of business. But not with Toyota and those communities from Racetrack. The sound and everything vroom vroom IS the source of the fun.

### Mild Hybrid?

It's a low SDM labeling for Hybrid when the market demands for it. Don't be fooled, that's just a name for **Idling Stop**. You cannot run the vehicle with its bed batteries alone.

Here on DNB, `Hybrid` (`Combustion` & `Electric` License Plate tag & back door label) requires the car can run in batteries alone atleast 25% of regular ICE mode. Otherwise, only `Combustion` is applicable, i.e. **Not considered Hybrid**.

### Idling Stop

since the motorcycles conceptions of it, Van Elektronische saved the ideas of the car that can automatically shut off engine when idling to save fuel in traffic jam. Which thankfully applicable finally in Racetrack.

All ICE powered (both ICE only & Tandem Hybrid) can shutoff engine when idling, like in scooters of the past, & that Suzuki car. And can seamlessly run again without a hitch. This indeed requires a brand new starter motor that's as strong and sturdy to handle this task. As the result all ICE Only Racetrack is as silent as its Hybrid version, because it uses same High Torque BLDC motor technology, just like those Idling Stop scooters and cars.

For Tandem Hybrids, even tho there is the big motor like it does with EV version, there's still the small ring motor. This is the starter motor that's now BLDC. It's used to start the engine and return from Idling Stop. Much lighterweight (lesser flywheel effect) & lower wattage than the big motor. And the cool part is when the big motor in Hybrid runs, the small motor can always become dynamo to reverse energy back to batteries of bed (Hybrid & EV) & acid (All), yey! Turns out that's what an Alternator does!  

### Regen Brake

Such big Small motor is crucial, because remember Regenerative Brake? When we experimented with Dynamoing, we indeed had reconfirmed that it caused resistance. Car makers have been using this discovery for such as Regenerative **Brake**, which is an assisted brake using said resistance from the motor being set to dynamo mode.

If we used the same big motor here, it will have an equally huge resistance and can stall the engine. So why not use the same starter motor since it's small hence has lesser resistance and almost equal to typical brushed Alternators?

### Simpler parts

Combining the motors as the result makes it easier to maintain.

We also have simplified other components too and reducing numbers of complexities everyday.

### Independence

But we do not over-combine essential components either. Such essential components are critical to the one to one functioning of the vehicles. It's not funny that all you have to hack is the infotainment and remotely control from there. Something still need to be disconnected to prevent said unauthorized exploits from being ran in the first place.

E.g., The infotainment is a separate computer with OBD built-in to give seamless effects of luxury cars alike. While it can set a setting, doing command temporarily connects extra OBD wires to the ECU to set the setting there and then disconnect it. Therefore, the ECU and Microcontroller Infotainment are 2 different things, like it used to be. Not only secure, but also sturdy. If you want to break the car, target the ECU, not the Infotainment.

Despite the independence, you can set settings from the infotainment alone, no need external OBD. You can share your config to others and download other's configs as well. Tune as you like!

### Tuning

Tuning is like how you'd tune Drones. You can use our Cardiotuners software and simulate your result. Once done, you can share and apply it to your car to test out the result. All you need to transfer is using a USB flashdisk way, copyparty wirelessly (turn on copyparty server on the infotainment and connect the WiFi to the same network as the builder), and more. When applying the file, the Infotainment will temporarily connect OBD, install the new setting, and unplug it again, leaving just the debug wires.

If something went wrong, don't panic. You can always reflash to default factory tunings at anytime, undeletable and always available as the first file. No factory reset required. This factory file can only be updated by firmware updates to the Infotainment.