# Klicky-Nozzle-Probe

Basically, this is a Klicky probe type that should only be used to do bed meshes.

Be advised, this is an experimental procedure and equipment, you can damage your printer or hurt yourself.
With that said, these procedures are working with my V2.4, and a v1.8 configured with klicky probe and Z auto calibration.

It is placed between the hotend nozzle tip and the bed, measuring then the bed distance to the actual nozzle without any offset that can cause issues when the extrusions are twisted.

With the regular klicky installed, do this for setup:

- change the probe offsets to 0 on klipper printer.cfg in the [probe] section, remember to comment the current probe offsets:
  - z_offset: 0
  - x_offset: 0
  - y_offset: 0

- then do:
  - G28
  - move the gantry some 60mm up and the toolhead to the front  
  - remove the "normal" klicky probe from the dock
  - place the nozzle probe on the toolhead magnets
  - M84
  - G28 (with the nozzle probe in place)

Now the printer will believe that the probe tip is the nozzle tip and will take care to avoid hitting the bed with the probe.
you can now a Quad Gantry Level or Z Tilt adjust to level the bed as much as possible.

You can now do the Bed mesh calibrate using your actual nozzle as the probing point.
After you are finished, don't forget to save your bed mesh and revert the probe offsets to the daily configuration.

Hope this has helped you.
