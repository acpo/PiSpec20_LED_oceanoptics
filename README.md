# PiSpec20_LED_oceanoptics
A Python interface for Ocean Optics spectrometers designed to proved the functions of a Spectronic 20 spectrophotometer including an LED light source
## Project Goals and Motivations  
The goal of this project was to replace the old Spec 20s in our teaching laboratories with equivalent functionality in 
modern equipment.  Choices of hardware and software were driven largely by familiarity.  The choice of the Raspberry Pi was 
to make an effectively disposable computer.  I picked Python 3.x (works on Python 2.7 also) for simplicity in migrating to different hardware.  What I created here is a simple frontend for the spectrometer suitable for use by relatively untrained undergraduate students.
## Project Audience  
The project was written to support undergraduate laboratories, so really this repository is for people looking for a frontend 
to run their spectrometer.  However, the functionality of the project can readily be expanded to take advantage of the 
spectrometer features.  This code takes care of collecting the spectra, everything else is just manipulations in code.  Simple changes in the code shift the interface from having lots of things chosen for you to needing to make lots of choices.
## PiSpec20 Requirements  
I wrote this on a Raspberry Pi 3b+. For Windows or Mac you will need to make small changes to the code to deal with OS peculiarities. You will need to possess an Ocean Optics spectrometer.  The LED requires building a small circuit to allow pulse width modulation of the LED for brightness control.  The schematic is below.  I built this on a Pi-topPROTO board which made it even easier.  
![schematic of PWM circuit for Raspberry Pi](https://github.com/acpo/PiSpec20_LED_stellarnet/blob/master/LEDCIRCUIT.png)
### Libraries  
- Python-Seabreeze  (https://github.com/ap--/python-seabreeze  or the Conda forge)  
- numpy  
- python-matplotlib  
- python-flask  
- python-virtualenv  
- Tkinter
- pigpio  
- *rarely needed* SeaBreeze  (https://sourceforge.net/projects/seabreeze/  depending on OS, you may need to build from source)  
### Files to install
- only one python file to get ¯\\_(ツ)_/¯  
- on Raspberry Pi remember to start the PWM daemon `sudo pigpiod`  
### Other Hardware  
- a USB connected Ocean Optics spectrometer  
- a PWM circuit and LED.  The easiest way to do this would be on a Raspberry Pi since it has PWM pins ready to use.  Other prototyping platfoms (Arduino, etc.) could be adapted easily.  From a 'standard' PC, a PWM circuit can be attached by USB (Yocto, etc.).  An acceptable LED for "white light" illumination can cost as little as $2.00.  
## Supported Devices  
### Directly tested  
| Manufacturer  | Spectrometer  | Works ?       |  
| ------------- | ------------- | ------------- |  
| Ocean Insight | HR 4000       |     yes       |  
| Ocean Insight | HR 2000 plus  |     yes       |  
| Ocean Insight | USB 2000      |     yes       | 

### Should work with SeaBreeze (Ocean Insight products)  
| Spectrometer | cseabreeze | pyseabreeze|  
| ------------ | :--------: | :--------: |  
|HR2000 |x | x |
|HR2000PLUS |x | x |
|HR4000 |x | x |
|JAZ |x | x |
|MAYA2000 |x | x |
|MAYA2000PRO |x | x |
|MAYALSL |x | x |
|NIRQUEST256 |x | x |
|NIRQUEST512 |x | x |
|QE65000 |x | x |
|QE-PRO |x | x |
|STS |x | x |
|TORUS |x | x |
|USB2000 |x | x |
|USB2000PLUS |x | x |
|USB4000 |x | x |
|USB650 | no | no |
|SPARK |x | x |  

## How to Help  
I don't write in Python for a living, nor particularly do a lot of programming.  And it shows in the code.  This is 
also a work in progress.  
If you wish to contribute please contact me.
## License  
MIT License.  This project relies on Python-Seabreeze which uses the MIT License.
