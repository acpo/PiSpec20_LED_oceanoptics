# PiSpec20_OceanOptics
A Python interface for Ocean Optics spectrometers designed to proved the functions of a Spectronic 20 spectrophotometer.
## Project Goals and Motivations  
The goal of this project was to replace the old Spec 20s in our teaching laboratories with equivalent functionality in 
modern equipment.  Choices of hardware and software were driven largely by familiarity.  The choice of the Raspberry Pi was 
to make an effectively disposable computer.  I picked Python 3.x (the older branch works on Python 2.7 also) for simplicity in migrating to different hardware.  What I created here is a simple frontend for the spectrometer suitable for use by relatively untrained undergraduate students.
## Project Audience  
The project was written to support undergraduate laboratories, so really this repository is for people looking for a frontend 
to run their spectrometer.  However, the functionality of the project can readily be expanded to take advantage of the 
spectrometer features.  This code takes care of collecting the spectra, everything else is just manipulations in code.  Simple changes in the code shift the interface from having lots of things chosen for you to needing to make lots of choices.  
There is a `def` in the code for saving spectra.  To make it accessible, you would just need to uncomment three lines in the GUI section to make a 'Save' Button visible.  
## PiSpec20 Requirements  
I wrote this on a Raspberry Pi 3b+.  The current version was updated on Python 3.9 and 3.11.  Raspbian OS *Bullseye* was used for testing.  The newer (in 2024) *Bookworm* OS also works but is slow on a 3b+.  
For Windows or Mac you will need to make small changes to the code to deal with OS peculiarities. You will need to possess an Ocean Optics spectrometer.  The LED requires building a small circuit to allow pulse width modulation of the LED for brightness control.  The schematic is below.  I built this on a Pi-topPROTO board which made it even easier.  
![schematic of PWM circuit for Raspberry Pi](https://github.com/acpo/PiSpec20_LED_stellarnet/blob/master/LEDCIRCUIT.png)  
*extra Windows requirement:  
[Visual C++ Build Tools](https://visualstudio.microsoft.com/visual-cpp-build-tools/) is required before installing Python-Seabreeze    
See the documentation at the [python-seabreeze documents](https://python-seabreeze.readthedocs.io/en/latest/install.html#operating-system-dependent-setup)*  
### Libraries  
- `pip3 install seabreeze`  (https://github.com/ap--/python-seabreeze  or the Conda forge)
- run the seabreeze setup script `seabreeze_os_setup` to add the udev rules
- `pip3 install numpy`
- `pip3 install matplotlib`
- (*May 2024*) may need to also get `sudo apt-get install python3-pil.imagetk` to address an import error from matplotlib  
- pigpio  {already part of Raspbian} (for Raspberry Pi control of the LED)

### Files to install
- only one python file to get ¯\\_(ツ)_/¯  
- on Raspberry Pi remember to start the PWM daemon `sudo pigpiod`.  Or permanently enable it with `sudo systemctl enable pigpiod`
- `sudo chmod +x run_hidden` to make the bash script executable. A batch file would substitute the bash script on Windows.
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
| Ocean Insight | USB 4000      | firmware issue? |

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
