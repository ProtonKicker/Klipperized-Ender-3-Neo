# Staring Gcode (edited)
M220 S100 ;Reset Feedrate
M221 S100 ;Reset Flowrate
M140 S[bed_temperature_initial_layer_single] ;Set final bed temp
M104 S[nozzle_temperature_initial_layer] ;Set final nozzle temp

G28 ;Home
BED_MESH_CALIBRATE 
M420 S1 ;Enable mesh leveling

G92 E0 ;Reset Extruder
G1 Z2.0 F3000 ;Move Z Axis up
G1 X10.1 Y20 Z0.28 F5000.0 ;Move to start position
M190 S[bed_temperature_initial_layer_single] ;Wait for bed temp to stabilize
M109 S[nozzle_temperature_initial_layer] ;Wait for nozzle temp to stabilize
G1 X10.1 Y145.0 Z0.28 F1500.0 E15 ;Draw the first line
G1 X10.4 Y145.0 Z0.28 F5000.0 ;Move to side a little
G1 X10.4 Y20 Z0.28 F1500.0 E30 ;Draw the second line
G92 E0  ;Reset Extruder
G1 E-1.0000 F1800 ;Retract a bit
G1 Z2.0 F3000 ;Move Z Axis up
G1 E0.0000 F1800
# Ending Gcode (stock)
G91                            ; Relative positioning
G1 E-2 F2700                   ; Retract a bit
G1 E-2 Z0.2 F2400              ; Retract and raise Z
G1 X5 Y5 F3000                 ; Wipe out
G1 Z10                         ; Raise Z more
G90                            ; Absolute positioning

G1 X0 Y0                       ; Present print
M106 S0                        ; Turn off fan
M104 S0                        ; Turn off hotend
M140 S0                        ; Turn off bed

M84 X Y E                      ; Disable all steppers but Z
