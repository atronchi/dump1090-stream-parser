# Azimuth and elevation tracking for a telescope.

I thought it would be fun to hack my telescope to track aircraft moving in the sky.

Hardware:
* [Celestron Omni XLT 150 on a CG-4 mount with motor drive kit $650](https://www.celestron.com/products/omni-xlt-150-telescope)
    * What are the 42PM48L(BZ) motor specs? A 42mm(NEMA17) motor with reduction gearing
    * ["The motors are rated at 19V, 1.27A and they are running at 6V, 0.35A only." "these motors are cheap low torque 7.5 degrees per step motors" "gearing of about 100 times"](http://www.iceinspace.com.au/forum/archive/index.php/t-42709.html)
        * Coil inductance 17Ohm printed on motor
        * Current capacity? Not printed, but OEM controller is 6V / 17Ohm = 353mA
    * [42PM48L motor specs](http://www.motionking.com/Products/PM_Stepper_Motors/42PM_Stepper_Motor.htm): 7.5 degree step, 4 phase, 19V, 1.27A, 15Ohm, 1100g.cm holding torque, 210g.cm deent torque, 9.6g.cm2 rotor inertia
    * [gear motor page](http://www.motionking.com/Products/PM_Stepper_Motors/PM_stepper_gear_motor.htm)
    * how many steps per turn are the motors geared for? 7.5 degrees per step / 100x reduction gearing = 0.075 degrees per step
    * how many turns per degree is the mount geared for?
    
* [Pre-assembled Stratux ADS-B unit with dual band radios, WAAS GPS, and AHRS $250](https://www.amazon.com/gp/product/B071HMQY19/ref=ox_sc_act_title_1?smid=A3TXMSIFSSB0X&th=1)
    * Mount the stratux unit to the telescope tube, aligning it to the telescope viewing direction so that the azimuth and elevation report consistent with where the scope is pointed
* [Waveshare stepper motor HAT for Raspberry Pi - $20](https://www.waveshare.com/wiki/Stepper_Motor_HAT)
    * Connect the HAT to the Pi and motors
* External 12VDC power (e.g. from a car battery)

* [Nooelec Stratux ADS-B Nano 2 starter bundle - $36](https://www.nooelec.com/store/sdr/stratux-bundle-nano-2-starter-edition.html)


Software:
* Modify dump1090-stream-parser to use current GPS location to compute azimuth and elevation to observed aircraft.
* Hack the dump1090 code to display current position and allow selection of target aircraft.
* Write a motor controller class that takes AHRS input for current telescope azimuth/elevation and drives the motors to acquire and track a target aircraft.
