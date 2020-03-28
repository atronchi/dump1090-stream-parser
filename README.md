# Azimuth and elevation tracking for a telescope.

I thought it would be fun to hack my telescope to track aircraft moving in the sky.

Hardware:
* [Celestron Omni XLT 150 on a CG-4 mount with motor drive kit $650](https://www.celestron.com/products/omni-xlt-150-telescope)
* [Pre-assembled Stratux ADS-B unit with dual band radios, WAAS GPS, and AHRS](https://www.amazon.com/gp/product/B071HMQY19/ref=ox_sc_act_title_1?smid=A3TXMSIFSSB0X&th=1)
    * Mount the stratux unit to the telescope tube, aligning it to the telescope viewing direction.
* [Waveshare stepper motor HAT for Raspberry Pi - $20](https://www.waveshare.com/wiki/Stepper_Motor_HAT)
    * Connect the HAT to the Pi and motors
* External 12VDC power (e.g. from a car battery)

* [Nooelec Stratux ADS-B Nano 2 starter bundle - $36](https://www.nooelec.com/store/sdr/stratux-bundle-nano-2-starter-edition.html)


Software:
* Modify dump1090-stream-parser to use current GPS location to compute azimuth and elevation to observed aircraft.
* Hack the dump1090 code to display current position and allow selection of target aircraft.
* Write a motor controller class that takes AHRS input for current telescope azimuth/elevation and drives the motors to acquire and track a target aircraft.
