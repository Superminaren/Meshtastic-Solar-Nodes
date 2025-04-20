# Solar node parts list - Updated Apr 2025

I will first lay out the document order in order for ease of access:
- I will put build examples in the node_types folder and link to them from here only as reference.
  Smaller parts, such as screws and adapters will be build specific, so electronics are the primary subject in this document.

- These are build examples. They are by no means perfect for every scenario and your use-case may require something different.

- I will write a short list of pros and cons with each build type.

## Builds
- [TheBamse's IP67 box-design.](./node_types/RAK_IP67_Box_TheBamse.md)
- TODO: Add more builds 

# Parts
There are a few key components you'd need when building a Solar node, but I will boil down the primary components below.
You can also click on the component names to get a more in-depth description of features.

## Microcontroller: 
The microcontroller is the heart of the operation and you won't get far without one.
The most common boards on the market today come with a LoRa transceiver chip built in, as well as a simpler antenna.
Most boards can be boiled down to two types:
- ESP32-based (Heltec, T-Beam, T-Deck, Station G1/G2, etc):
Powerful dual-core processors, but high power consumption, not recommended for solar nodes unless large solar panels are used.
Have been running slightly more stable in recent versions of meshtastic. Most have a screen built in as well as onboard WiFi.
- nRF52-based (RAK, T-Echo):
Extremely power efficient processor, but at the cost of less memory, no WiFi, and (when buying bare boards) no screen built in.

## Battery:
Just like with a microcontroller, you can't get far without a battery unless you power your node from USB indefinitely.
There are plenty of choices on the market here, but for most people I'd recommend starting with the Lithium Ion (Li-Ion) or Lithium Polymer (LiPo).
- Lithium Polymer:
  One of the more common battery types. Almost always a pouch and some people rightfully call these "Spicy Pillows" due to them having very little protective features.
  They have a decent energy density, but are mostly known for being sold in handy shapes which fit into handheld devices. Don't puncture one though, or you will have a fire.

- Lithium Ion:
  Sibling of Lithium Polymer which usually comes in cylindrical metal cells (18650, 21700), has a higher energy density and are harder to puncture but should still be treated as a fire hazard.

- Nickel–metal Hydride (NiMh):
  Common type of cell which is practically inert when compared to other types. They are usually rechargeable but have the con that their voltage range usually makes them incompatible with modern devices.
  There are applications for these however, especially in winter-resilient nodes. But for most people I'd recommend sticking with Lithium Ion or Lithium Polymer.

- Lithium Titanate (LTO):
  Expensive cell type which is chargable even in -40C, however these have a few drawbacks such as the inability to charge them with regular chargers and the lower energy density. These would only work in complex node setups with dedicated circuits for charging and discharging.

## Solar Panels
What would a solar node be unless it had a solar panel? There are a few type of cells as well as voltage ranges, but I will round down to the most common types here:

- [Monocrystalline](./hardware_description/solar_cells/monocrystalline.md):
  The superior alternative, a bit more expensive but with higher output in all scenarios. 

- [Polycrystalline](./hardware_description/solar_cells/polycrystalline.md):
  Cheaper alternative which might work in less demanding situations.

Solar voltage levels:
You'll likely be looking at 5/6-volt panels when building a solar Meshtastic node, this keeps components cheap as well as easily available.
There are ways to apply larger panels made for 12V+, but you'll be sacrificing efficiency stepping this down to acceptable voltages for the microcontroller and charging circuits.

## Charging Circuits
