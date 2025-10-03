# MINTS PCB Onboarding with KiCAD  

This document is a **step-by-step guide** to help new MINTS members learn how to use **KiCAD** for PCB design.  
It covers setup, workflow, best practices, and useful resources.  

📖 For even more details, you can also consult the textbook: [KiCAD Like A Pro](https://www.gods69.com/download/KiCadLikeaPro3e_Course_Companion.pdf).  

---

# 1. Setting Up KiCAD  

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

---

# 2. General KiCAD Workflow Overview

Designing a PCB in KiCAD generally follows this four-stage workflow:

   1. Schematic Capture (Eeschema) – Draw your circuit.

   2. Footprint Assignment – Link schematic symbols to physical packages.

   3. PCB Layout (PCBNew) – Arrange components and route traces.

   4. Fabrication Outputs – Generate files for manufacturing and assembly.
      ![General Workflow](workflow.png)

---

# 3. Detailed Workflow

## A. Schematic Design

   1. Start a new project: File → New Project.

   2. Add components (A hotkey).

   3. Wire connections (W hotkey).

   4. Use labels (L) instead of drawing long wires.

   5. Annotate the schematic: Tools → Annotate Schematic.

   6. Run ERC (Electrical Rules Check) to catch errors.

Use global labels (like VCC, GND) for power nets instead of wiring them everywhere.
If you want your schematic to look more presentable, watch this [video](https://www.youtube.com/watch?v=szu8dJoyikA&list=PLn6004q9oeqGl91KifK6xHGuqvXGb374G)

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

---

# 📦 4. Generating Gerber and BOM Files with Plugins  

In MINTS, we recommend using plugins to streamline the process of exporting **Gerber files** (for fabrication) and **BOM files** (for assembly).  

Two key plugins you should install and use are:  

- **NextPCB Plugin** → simplifies Gerber file generation and upload.  
- **Interactive HTML BOM (iBOM)** → generates an interactive bill of materials for assembly and debugging.  

---

## 🖨️ A. NextPCB Plugin for Gerber Files  

1. Open your PCB in **PCBNew**.  
2. Go to **Tools → External Plugins → Plugin and Content Manager**.  
3. Search for **NextPCB** and install the plugin.  
4. After installation, you’ll see a **NextPCB button** in PCBNew.  
5. Click it, and the plugin will:  
   - Automatically generate the required **Gerber files** and **drill files**.  
   - Package them into a `.zip` file.  
   - Open NextPCB’s website for order submission (optional).  

Even if you use a different manufacturer (e.g., JLCPCB, PCBWay), you can still use the NextPCB plugin just to generate the correctly formatted Gerber `.zip`.  
For more details on generating gerber files, watch this [video](https://www.youtube.com/watch?v=C_UdqlUmDNA)

---

## 📑 B. Interactive HTML BOM (iBOM)  

The iBOM plugin creates a **clickable, interactive BOM** with board previews, which is extremely useful for assembling and testing boards.  

### Installing iBOM  

1. Open **Tools → External Plugins → Plugin and Content Manager**.  
2. Search for **InteractiveHtmlBom** and install it.  
3. Restart KiCAD if necessary.  

### Using iBOM  

1. In **PCBNew**, go to:  
   - **Tools → External Plugins → Interactive HTML BOM**  
2. Configure options:  
   - Select output as `HTML`.  
   - Include footprints, references, and component values.  
   - Enable highlighting when clicking components.  
3. Export → This will generate an `.html` file in your project directory.  
4. Open the `.html` file in your browser:  
   - Left pane → BOM list.  
   - Right pane → PCB preview (clicking a part highlights it).  

This is very useful when soldering by hand or debugging, since you can search for a component and instantly locate it on the PCB.  

---

# 6. Customization and Terminology  

As you get more comfortable with KiCAD, you’ll need to create **custom components**, import special footprints, and adding **MINTS logo** to your PCB. This section explains how.  

---

## A. Creating Custom Symbols  

Symbols represent components in the **schematic editor**. If a part you need doesn’t exist in the standard libraries:  

1. Open the **Symbol Editor**:  
   - **Tools → Symbol Editor** (from schematic view).  
2. Create a new library (if you don’t already have one).  
3. Add a **new symbol**:  
   - Define pins with proper numbering and electrical type.  
   - Add fields (name, value, footprint association).  
   - Draw the symbol body (rectangle, circle, etc.).  
4. Save to your **personal library** (separate from KiCAD default libraries).  

⚡ **Tip:** Always double-check pin numbering with the part’s **datasheet** before using your symbol in a design.  

---

## B. Importing or Creating Custom Footprints  

Footprints define the **physical layout** of a part on the PCB.  

1. Open the **Footprint Editor**:  
   - **Tools → Footprint Editor** (from PCBNew).  
2. Create a new footprint:  
   - Place pads (SMD, through-hole).  
   - Define courtyard, fab layer, and 3D model if available.  
   - Name footprint clearly (e.g., `QFN-32-0.5mm`).  
3. Importing footprints:  
   - Download `.kicad_mod` or `.pretty` libraries (common from GitHub repos, manufacturer sites).  
   - Add them via **Preferences → Manage Footprint Libraries**.  

⚡ **Tip:** Manufacturers like **Texas Instruments, Microchip, ST** often provide KiCAD footprint libraries or 3D models for their parts.  

---

## C. Adding Custom Silkscreens (Logos & Graphics)  

Silkscreen is the **printed text/graphics** on the top/bottom of a PCB (white ink on real boards). You can add **logos, labels, or artwork**:  

1. Prepare your logo/graphic in **SVG** format (or monochrome bitmap).  
2. Use the plugin **Bitmap2Component** (bundled with KiCAD):  
   - Convert the image to a footprint or graphic.  
   - Place it on the **Silkscreen Layer (F.SilkS / B.SilkS)**.  
3. Alternatively, draw text and shapes directly in **PCBNew** on silkscreen layers.  

⚡ **Tip:** Keep silkscreen clear of pads and vias, otherwise the fab house may clip or delete it.  

---

## 📖 D. General Terminology  

Here’s a quick glossary of terms you’ll hear a lot in PCB design:  

- **Schematic (SCH)** → The logical circuit diagram.  
- **Symbol** → A 2D schematic representation of a component.  
- **Footprint** → The physical pad layout for a component.  
- **Net** → A logical electrical connection (wire).  
- **ERC (Electrical Rules Check)** → Verifies schematic errors.  
- **DRC (Design Rules Check)** → Verifies PCB spacing, clearances, etc.  
- **Gerbers** → Industry-standard files used by PCB manufacturers to fabricate boards.  
- **BOM (Bill of Materials)** → A list of all components used in a design.  
- **Silkscreen** → Printed text/graphics on PCB surface (labels, logos).  
- **Copper Layer** → The conductive trace layer of the PCB.  
- **Via** → A plated hole connecting copper layers.  
- **Ground Plane** → A filled copper area connected to ground.  

---

# 🌍 7. Next Steps for New Members  

(continues as before…)  


