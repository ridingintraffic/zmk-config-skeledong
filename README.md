# zmk-config

This repository contains my zmk configuration for [BastardKB's Skeletyl](https://github.com/Bastardkb/Skeletyl) using [Nice!Nanos](https://nicekeyboards.com/nice-nano/) and a [Seeed Studio XIAO nRF52840](https://www.seeedstudio.com/Seeed-XIAO-BLE-nRF52840-p-5201.html) in dongle mode.

Skeletyl config is forked from [0xcharly](https://github.com/0xcharly/zmk-config), keymap still work in progress.

# how to pair multiple skeletyl boards to a single dongle.  
i have a few wireless skeletyl and it is damn nice to have them all paired to the same dongle if i want to switch between things.  
how do you do that.  
this is simple.  
however it is methodical.  
be particular about the order of operations and pay attention.  

# pairing multiples  
assumptions:  
you have one dongle.  
you have 2 skeletyl left boards that share the same controller and keymap  
you have 2 skeletyl right boards that share the same controller and keymap  
we will name the first set 1-skeletyl-left, 1-skeletyl-right  
we will name the second set 2-skeletyl-left 2-skeletyl-right  
-- code requirements.   
``` 
skeletyl_dongle.conf 
# how many can i connect to 
# i am reading this as how many total so for us to use two sets it would be 4
CONFIG_ZMK_SPLIT_BLE_CENTRAL_PERIPHERALS=4
CONFIG_ZMK_SPLIT_ROLE_CENTRAL=y
```

```
<begin>  
0.  you have nothing paired but you have the dongle and the boards. 
 - all boards should be powered off.
1. flash the settings reset on the dongle.    
2. flash the dongle firmware to the dongle.    
3. power on 1-skeletyl-left  
4. flash the settings reset on 1-skeletyl-left.    
5. flash the firmware on  1-skeletyl-right.    

6. power on 1-skeletyl-right  
7. flash the settings reset on 1-skeletyl-right.   
8. flash the firmware on  1-skeletyl-right.    
  - verify that 1-skeletyl-left and 1-skeletyl-right are connected to the dongle and functioning   
9. power off 1-skeletyl-left 1-skeletyl-right  
10. power on 2-skeletyl-left  
11. flash the settings reset on 2-skeletyl-left.  
12. flash the firmware on  1-skeletyl-right.    
13. power on 2-skeletyl-right  
14. flash the settings reset on 2-skeletyl-right.  
15. flash the firmware on  2-skeletyl-right.   
  - verify that 2-skeletyl-left and 2-skeletyl-right are connected to the dongle and functioning  
16.  now when you power on either board they will all bond with the single dongle.   you can mix and match left and right cause it doesnt care.  
<end>
```