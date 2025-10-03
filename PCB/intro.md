# MINTS PCB Onboarding with KiCAD

# welcome to MINTS!

This document is a guide to learn about using KiCAD software for PCB design. For even more details you can also consult the textbook: [KiCAD Like A Pro](https://www.gods69.com/download/KiCadLikeaPro3e_Course_Companion.pdf)

# Setting Up KiCAD

### Installing KiCAD

download the latest version from the [KiCAD website](https://www.kicad.org/download/). make sure to choose the latest stable release near your region.
On linux, use your package manager to install it (e.g. sudo apt install kicad)

### Setting up libraries

now with KiCAD installed we need to install some symbol libraries that we commonly use when designing PCBs. 

Clone the following repositories into a known folder:
	*[Digi-key Symbol/Footprint Library](https://github.com/Digi-Key/digikey-kicad-library)
	*[Sparkfun Symbol/Footprint Library](https://github.com/sparkfun/SparkFun-KiCad-Libraries)
Add Libraries via:
		**Preferences** -> **Manage Symbol Libraries**
		**Preferences** -> **Manage Footprint Libraries** 
then add all of the symbol files to your KiCAD symbol library and all the Footprint files to your KiCAD footprint library.

### Setting up Plugins








