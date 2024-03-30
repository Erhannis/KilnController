Kiln controller PCB, in KiCAD.  ESP32, controlled (potentially) over wifi.

<img alt="PCB Diagram, from JLCPCB" src="5335756894208-Produce_DanZhi.SMT_Snapshot.Top.6176162A_Y20.SMT02401121555625.png" width="300" />

# Instructions 
Comes with two thermocouple readers and controls three heating elements.  Attach thermocouples to appropriate points, attach three SSR-DA60 to HEAT1-HEAT3 and another to ALL_POWER, wire in 240V (see instructions on board), recommended don't attach USB while mains voltage is connected; the 5V sources might conflict - also just seems a little unsafe.  The board is shaped to match my Everheat Classic 1210 frontplate - hopefully it fits, haha.  You can reshape it if you want, or just run wires to your thermocouples and elements.  The Main TC is for inside the kiln (PIDKiln has a link to a sturdy thermocouple), the Aux TC is for the kiln outside surface (I think it's optional?).  I broke out all 6 unused GPIO pins.  See [code](#code) for firmware.

Warning: if any elements are active, all elements are live at >= 120V.  There's a blue LED that lights up when any element is active; watch out for the blue LED.  ALSO!  I hear that SSRs can fail closed, meaning the elements may stay live even once the blue LED turns off.  So...maybe just unplug the thing if you're gonna touch the coils.

# Code
See my fork of PIDKiln at https://github.com/erhannis/PIDKiln
Note that in order to flash the code, the board must be unpowered to start, you need to connect BOOT to GND, plug the board in via USB, and then you have a handful of seconds to initiate a data transfer at 115200 baud (either the main code flashing, or the "ESP32 Sketch Data Upload").  Try turning on Arduino IDE logs for compilation and upload, then copy the relevant upload command into the terminal, for timing.  Afterward, remove boot jumper and replug the board.

Disclaimer: I have no formal electronics training, and this thing connects to 240V, so like, maybe use this thing away from anything flammable, and on your own head be the results.  And DON'T TOUCH THE COILS WHILE IT'S HEATING!  Because they're live 240V, and also may be hot.

# Additional parts
Thermocouple: https://www.auberins.com/index.php?main_page=product_info&cPath=20_3&products_id=39
  (Also one of the cheap k-type thermocouples from amazon, for the case.  Though, see notes.)
Bus blocks: https://www.amazon.com/dp/B0B2L7QBVN
Heat sinks: https://www.amazon.com/dp/B08ZCYBPTV
SSRs: https://www.amazon.com/dp/B01MSTFKIP (60DA)
  Note that (according to tests) these start and stop conducting at zero volt crossings.  Also, they still let like 2mA through while open, which CAN yield high voltages.
  You might get away with lower amp ones.

# Notes
I picked the slightly more expensive thermocouple readers, which (supposedly) are more accurate and support multiple thermocouple types instead of just K - just in case that turns out to be useful.  If you're not using k-type, though, you'll probably need to tweak something in code to tell the controllers so.
I had trouble where at high temperatures, the readings on both thermocouples would go nuts.  This stopped happening after I hung the case thermocouple away from contact with anything else.  I am baffled as to how that could have happened.

MIT license.

-Erhannis

Btw, I have like 4 extra from the manufacturing batch if anybody want to buy one for like, I dunno, $100, say.  (You'll have to add the SSRs and bus terminals yourself, though.)  Getting 5 boards assembled from JLCPCB costs around $330 total.
(If you're up for soldering the ESP32 WROOM module yourself (difficult), you can use Economy mode instead of Standard and save like $100.)
