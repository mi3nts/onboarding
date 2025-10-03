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
