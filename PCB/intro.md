# MINTS PCB Onboarding with KiCAD  

This document is a **step-by-step guide** to help new MINTS members learn how to use **KiCAD** for PCB design.  
It covers setup, workflow, best practices, and useful resources.  

📖 For even more details, you can also consult the textbook: [KiCAD Like A Pro](https://www.gods69.com/download/KiCadLikeaPro3e_Course_Companion.pdf).  

---

1. Setting Up KiCAD  

## Installing KiCAD  

- Download the latest version from the [KiCAD website](https://www.kicad.org/download/).  
- Choose the **latest stable release** closest to your region.  
- On Linux, you can install via your package manager:  

```bash
sudo apt install kicad
```
for more details on installion, watch this [video](https://www.youtube.com/watch?v=szu8dJoyikA&list=PLn6004q9oeqGl91KifK6xHGuqvXGb374G)

## Setting Up Libraries

Libraries contain the symbols (schematic components) and footprints (physical pads and packages) needed for PCB design.
1. Clone the following commonly used libraries:

   - Digi-Key Symbol/Footprint Library

   - SparkFun Symbol/Footprint Library

2. Add libraries in KiCAD:

Go to:

 - Preferences → Manage Symbol Libraries

 - Preferences → Manage Footprint Libraries

Add all symbol files to the Symbol Library.
Add all footprint files to the Footprint Library.

Always verify the footprint dimensions against the part’s datasheet before ordering boards!

## Setting Up Plugins

KiCAD supports plugins to make design easier. Some recommended plugins:
 - PCBWay integration → automates the process of preparing and submitting PCB designs for manufacturing and assembly with the company PCBWay

 - Interactive HTML BOM → generates interactive BOM files for assembly.

 - Fabrication Toolkit → automates the process of generating manufacturing files for printed circuit boards (PCBs)
   
 - NextPCB → simplifies the PCB ordering process by allowing users to get real-time quotations and place orders for fabrication directly within the KiCad software

Install plugins via the Plugin & Content Manager (KiCAD 7+), or manually copy them into the ~/.local/share/kicad folder (Linux) or equivalent on Windows/macOS

# 2. KiCAD Workflow Overview

Designing a PCB in KiCAD follows this four-stage workflow:

   1. Schematic Capture (Eeschema) – Draw your circuit.

   2. Footprint Assignment – Link schematic symbols to physical packages.

   3. PCB Layout (PCBNew) – Arrange components and route traces.

   4. Fabrication Outputs – Generate files for manufacturing and assembly.

# 3. Detailed Workflow

## A. Schematic Design

   1. Start a new project: File → New Project.

   2. Add components (A hotkey).

   3. Wire connections (W hotkey).

   4. Use labels (L) instead of drawing long wires.

   5. Annotate the schematic: Tools → Annotate Schematic.

   6. Run ERC (Electrical Rules Check) to catch errors.

Use global labels (like VCC, GND) for power nets instead of wiring them everywhere.

## B. Assigning Footprints

Each schematic component must be assigned a physical footprint.

   - Open: Tools → Assign Footprints.
   - once here you can assign each symbol a footprint from your local footprint library
   - for more details on navigating the UI, watch this [video](https://www.youtube.com/watch?v=JMa9q4YhRDk)
   - Save your work!

Always double-check pinouts against datasheets — footprints are one of the most common mistakes in PCB design.

## C. PCB Layout (PCBNew)

1. Import schematic: Tools → Update PCB from Schematic.

2. Place components:

   - Group related parts together.

   - Keep connectors near board edges.

   - Place decoupling capacitors close to IC power pins.

3. Route traces:

   - Start with power and ground.

   - Use 45° angles, not 90°.

   - Keep traces short and direct.

4. Add ground plane: Add Filled Zone → GND.

   - Run DRC (Design Rule Check) to find clearance/trace width issues.

Route critical nets first (clocks, power lines, high-speed signals) before filling in general routing.


