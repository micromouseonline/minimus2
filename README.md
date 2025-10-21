# MINIMUS-2
A half size micromouse design.

## Intent

Create hardware and software for a half-size micromouse robot. The design should be simple and easy to reproduce. It is not necessarily meant to compete at the highest levels. Rather, it should provide a working platform for beginners while still forming the basis for more performant derivatives.

As with many of my projects, a key aim is to lay the foundation for a competitive robot in the future and so there seems little point in overly constraining the design.

### Mechanical

 1. The chassis will be based on the PCB which will be 0.8mm FR4. 
 1. Dimensions should not exceed 50mm x 40mm.
 1. Motor mounts will be 3D printed. Ideally using SLA (resin) techniques though FDM should be an option.
 1. The differential drive will be by means of two wheels to leave space for a suction fan
 1. The initial design will not incorporate a fan but allowance should be made at all times for the possibility of adding a fan at a later date.
 1. Motors will be commonly available 6x12mm coreless types.
 1. Gears are readily available as 8+54 tooth 0.3mod pairs intended for small drones. That leaves the wheels larger than ideal (> 18mm diameter). A tradeoff for availability.
 1. Wheels will need to be SLA printed to engage with available drive gears.
 1. Tyres could be deNano types but o-rings or similar are likely to prove suitable at this stage.

### Sensors

 1. Wall sensors will use four pairs of IR or visible light reflective devices. Emitters may need to be 5mm diameter though 3mm types are to be preferred. Narrow beam emitters are coupled with detectors having a wider acceptance angle.  These whould be as simple as possible.
 1. An IMU having at least 6 axes (3*gyro + 3*accel) will provide feedback for rotational motion. The accelerometers may prove necessary for velocity estimation, crash detection and user input.
 1. Wheel encoders are the promary inputs for linear odometry and also make useful user input devices. High resolution magentic angle sensors may be fitted to the main wheels with the sensor carriers vertical on the PCB behind the motor mounts. Magnetic shielding for the motors may be needed. Lower resolution encoders 1. possibly optical 1. may be effective if used with the IMU.
  
### User IO

 1. There should be at least one user button in addition to the processor reset. This button may also be used to place the processor into bootloader mode at power up if necessary/appropriate. The ESP32 processor are likely to need this.
 1. All otherwise unused pins should have LEDs attached for state and/or operating mode indication. Neopixel devices are useful if there is support available. If space permits, an I2C LED driver might be an option.
 1. Debug (SWD) and serial connections are essential during development. These must be reliable but have low insertion force and relatively long cycle life.
 1. A small buzzer is often useful if space permits.
 1. A pluggable display would be a great addition. Conceivably it could be a pass-through for the debug/programming connector.
 1. A radio link might be substituted for a display. Perhaps all these could be stacked for development and removed for contest runs.

### Electrical

 1. Power should come from 1 or 2 LiPo cells. A single cell might be sufficient but it is best to allow for more in the design. Space must be left for two cells in the mechanical layout.
 1. Care must be taken to find suitable cells that are likely to have a long availability.
 1. Cells should have individual connectors for greatest flexibility.
 1. Connectors are likely to need modification for low insertion force as cycle life is often low.
 1. Try to find commonly used connectors such as those used in micro drones. These are very fiddly to make by hand. Prefer ready-made.
 1. Run times can be long so cell capacity will need careful consideration.
 1. Power switching will need a mechanical switch and high-side MOSFET as suitably sized switches do not have sufficient current carrying capacity.


### Processor

 1. A 32 bit processor seems inevitable. It should run C++ code and, for those who must, MicroPython.
 1. Emphasis should be given to maximising available RAM and the availability of non-volatile storage. 
 1. Flash sizes should exceed 512K for flexibility.
 1. At least one SPI and one I2C peripheral will be needed to accomodate the IMU
 1. Ideally, two hardware quadrature input channels will be available or should be possible using interrupts. If the same pins can be used for SPI, in addition to the IMU, then that would provide greater flexibility in the choice of encoder topology. Note that some optical encoder designs might need analogue inputs.
 1. There should be a suitable debug interface that will work with commonly available tools like openOCD.
 1. For power saving, it should be possible to activate a low power or standby mode. This may be as simple as reducing the processor clock.
 1. It would be most convenient, for C+++ development, if the processor is supported by PlatformIO. Like it or not, this provides a great deal of flexibility. Not least in the choice of available development environments across platforms.
 1. Support for the Arduino framework, while not giving the highest performance, would greatly simplify the portability of the code.
 1. Early adoption of an RTOS might bring benefits. It is automatically available for the ESP32 and easy to implement for the STM32
 1. Processor choice seems likely to be between STM32F413 and ESP32. Both provide all the required features. Ready built breakout boards are unusally rare in this size. STM32F413RGT and ESP32-PICO placed directly on the board are the most space efficient. ESP32 modules can be compact and provide wireless links but are still quite large and may mean a dual board configuration. Of course, with care, the entire processor could be on a (probably custom) carrier.
  
### Assembly

 1. Given the size of the robot, it is going to require SMT devices. Some of these are hard to mount without some experience. IMUs and motor drivers in particular are usually tiny, leadless devices. It should be assumed that boards will be pre-assembled by services such as PCBWAY or JLCPCB. The higher cost is likely to be easily offset by improved reliability, reduced frustration and the removal of a requirement to hold stocks of components locally.
 2. A pre-assembled board should maximise the cost benefits by having as much circuitry as possible mounted at manufacture. That includes encoders and, if appropriate, sensor carriers with all but the optical devices already mounted. 
 3. It may be a good idea to include chargers and/or serial interface options at the same time.
 4. Groups purchases are probably the way to go.
 5. Fasteners must be readily avaiable and robust.
 6. Bearings, axles and retainers can be a challenge. All must be readily available with little or no modification. For example, axle shafts will ideally be available in the right length without cutting. Good push fits can be surprisingly effective at these scales.