# KiCAD design files for Minimus

All ECAD work is done wih KiCad V8.0

## Libraries

 - Add the JLCPCB parts library by following the instructions here:
    https://github.com/CDFER/JLCPCB-Kicad-Library

    This library contains all the basic parts avaiable from the JLCPCB assembly service, inclluding their footprints and part references.

    As far as I know, the library source is updated every day but the local copy is not so all parts should be checked at the time of a request for manufacture.

    Updates can be done manually from the Plugin manager.

    Since the library is a git repository, it might be possible to clone or fork it, create a local branch and edit the footprints that way.

 - There will also be a custom project library for the parts used in minimus.

## Plugins

 - Add the KiCAD JLC PCB Tools by following the instructions here
     https://github.com/Bouni/kicad-jlcpcb-tools


## Schematic Style

Note that the symbols used by the JLCPCB parts library do not match the symbols that are the default in KiCAD supplied libraries. The most important attributes are all those relating specifically to the JLCPCB part - size, part number, type and so on. If the symbols are a problem, it might be best to copy each part from the JLCPCB library to the project library and edit the symbol there.


## PCB Style

For a half-size mouse, all the components are small and contained in a small PCB. It is not practical to have the component reference and value for all parts. If the boards are to be manufacured by a service, this is not a great problem. A reference diagram showing the part placement from the FAB layers would be helpful for testing and debugging.




