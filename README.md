# Klicky-Nozzle-Probe

This is a Klicky probe type that should only be used to do bed meshes.
It is placed between the hotend nozzle tip and the bed, measuring the bed distance to the actual nozzle.

<p float="left">
  <img src="/Photos/Nozzle_Probe.png" width="150" />
  <img src="/Photos/front.jpg" width="150" />
  <img src="/Photos/side.jpg" width="150" />
  <img src="/Photos/nozzle_probe_docked.jpg" width="150" />
</p>

The objective is to prevent the probe offset to in conjunctin with any twisting on the extrusions or rails to make the nozzle too close or too far away even with a bed mesh.

Be advised, this is an experimental procedure and equipment, you can damage your printer or hurt yourself.
With that said, these procedures are working with my V2.4, and a v1.8 configured with [Klicky Probe](https://github.com/jlas1/Klicky-Probe) and [automatic Z calibration](https://github.com/protoloft/klipper_z_calibration).

With the regular klicky installed, do this for preparation:

# BOM
- 1x microswitch (the omron D2F-5 or D2F-5L (removing the lever is necessary)
- 2x M2x10 self tapping
- 4x 6x3 magnets

# Instructions
- print the model
- install the magnets and switch cables as in the original Klicky Probe
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

This is from user Yeri on Voron Discord that helped testing this approach.
- Before (using "normal" Klicky probe)
<img src="/Photos/BedMesh_before_Yeri.png" width="600">
- After (with Nozzle Klicky probe)
<img src="/Photos/BedMesh_after_Yeri.png" width="600">
