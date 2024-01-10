Kiln controller.  ESP32, controlled over bluetooth.  (Assuming I don't change my mind before writing the code.)

##  WARNING: heating elements are live AT ALL TIMES that the controller is plugged into mains!  Even when cold!
They are only controlled at one end; the other is connected straight to one half of the 240v system.  (Unless you wire yours differently.)
//RAINY Maybe fix that....

Comes with two thermocouple readers and controls three heating elements.  Attach thermocouples to appropriate points, attach three SSR-DA60 to HEAT1-HEAT3, wire in 240V, recommended don't attach USB while mains voltage is connected; the 5V sources might conflict - also just seems a little unsafe.  The board is shaped to match my Everheat Classic 1210 frontplate - hopefully it fits, haha.  You can reshape it if you want, or just run wires to your thermocouples and elements.

Disclaimer: I have no formal electronics training, and this thing connects to 240V, so like, maybe use this thing away from anything flammable, and on your own head be the results.  And DON'T TOUCH THE COILS WHILE IT'S PLUGGED IN!

MIT license.

-Erhannis
