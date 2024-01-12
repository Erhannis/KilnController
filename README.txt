Kiln controller.  ESP32, controlled over bluetooth.  (Assuming I don't change my mind before writing the code.)

Comes with two thermocouple readers and controls three heating elements.  Attach thermocouples to appropriate points, attach three SSR-DA60 to HEAT1-HEAT3 and another to ALL_POWER, wire in 240V, recommended don't attach USB while mains voltage is connected; the 5V sources might conflict - also just seems a little unsafe.  The board is shaped to match my Everheat Classic 1210 frontplate - hopefully it fits, haha.  You can reshape it if you want, or just run wires to your thermocouples and elements.  I included the second thermocouple just in case; I probably won't write control code for it, but YOU can if you want.  I likewise broke out all 6 unused GPIO pins.

Warning: if any elements are active, all elements are live at >= 120V.  There's a blue LED that lights up when any element is active; watch out for the blue LED.

Disclaimer: I have no formal electronics training, and this thing connects to 240V, so like, maybe use this thing away from anything flammable, and on your own head be the results.  And DON'T TOUCH THE COILS WHILE IT'S HEATING!  Because they're live 240V, and also may be hot.

MIT license.

-Erhannis

Btw, I may end up with a few extra from the manufacturing batch if anybody want to buy one for like, I dunno, $100, say.  Getting 5 from JLCPCB costs around $330 total.
