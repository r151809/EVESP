# EVESP
ESP32 (Lolin32) based EV charge controller
Implement charging controller according to SAE J1772 (https://en.wikipedia.org/wiki/SAE_J1772) and relay driver.

Project maturity: just schematics (no testing nor SW yet)!

Only fixed cables are supported (no PP support).

Recidual current (AC+DC) protection is planned with https://deltrixchargers.com/wp-content/uploads/2019/10/WA-DS-015-RCM14-03-Rev-B.pdf
https://www.stegen.com/nl/ev-producten/126-residual-current-sensor.html

Three relays, one for each phase. This is inteded for cases when there is unsymmetrical load in the house, and you still want to charge the car (maybe there is another car charging in one phase already). Another usecase is cars that go to sleep when not charged, and while sleeping they do not accept pre heat commands from the cloud. My take for that would be charging with single phase with 6A current, instead of not charging at all, full 3-phase charging only when you really want to charge. Changing the phases on the fly might not be supported by cars, but that is easy to overcome by stopping the charge before switching on/off any phases.

Misc features:
4 local LEDs
8 IO for external LEDs or buttons
1 up to 12 V LED output for lighting up the charging cable dummy socket (where you keep the cable when it's not connected to car)  

Many ideas (component selection) of the schematic are taken from https://github.com/SmartEVSE/smartevse and from http://www.analogevse.xyz/AnalogEVSE-en.html. 

PWM generation and Wifi connectivity is handled with LoLin32-board:
https://wiki.wemos.cc/products:lolin32:lolin32
It's discontinued already, but you can still find them from ebay.
Pinout is here: https://arduino-projekte.info/wemos-lolin32/

Security:
SW cannot enable relay drivers unless RCM is happy and CP is connected to some load. So the design should be safe in case of forced disconnect and any ground leakage.

Manufacturing of the first PCB patch will be done by Itead.cc. 

## Copying
Feel free to copy anything I have added to this project. If it is not too much to ask, please let me know what you are doing (it's not mandatory) :). Also any bug's would be nice to know.