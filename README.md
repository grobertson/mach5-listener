# mach5-listener
Listen via UDP for valid commands from client switchboxes

***VERY INSECURE/RUDIMENTARY IMPLEMENTATION, USE AT YOUR OWN RISK***

My experimental "controller" for DIY cockpit switchboxes. mach5-listener takes commands from remote clients (typically an ESP8266 or ESP32 microcontroller) which trigger keyboard presses on the local machine. 

### TODO:

Everything

### Notes

*Security can be handled in lots of ways, this implementation ignores them all. Currently my own setup keeps everything mach5 related on a dedicated wLAN, and forces mach5-listener to bind only the specified (private, non-routed) network interface.*

Commands are verb/noun pairs which represent in-game controller key mappings. i.e. verb examples "LIGHTS\n" or "TURBO_DECREMENT\n" are simple verbs requiring no noun (parameter). Where a parameter is required, the pair is seperated by a colon ":", and the command ends with a newline character. Nouns/parameters aren't needed for 99-99.9% of in-game commands because they are almost always boolean toggles -- implementing "LIGHTS:ON\n" would require knowing/tracking the current state of the headlights, which opens a pandora's box of questions and would be highly game-specific. 
