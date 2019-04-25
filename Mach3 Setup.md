# Mach3 Setup
## Windows 7 Notes
[Mach3 will crash windows 7 after certain updates](https://support.machmotion.com/books/knowledge-base/page/mach3-shutting-down-pc-on-launch)

To fix this, launch cmd.exe as administrator and run the following lines:

    reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\Memory Management" /v FeatureSettingsOverride /t REG_DWORD /d 3 /f

    reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\Memory Management" /v FeatureSettingsOverrideMask /t REG_DWORD /d 3 /f

## Mach3 Ports and Pins settings for TB6600HG driver

##### Motor Outputs:
Signal |Step Pin# | Dir Pin#
-------|----------|---------
X Axis | 2        | 3
Y Axis | 4        | 5
Z Axis | 6        | 7

##### Output Signals
Signal    | Enabled | Pin Number | Active Low
----------|---------|------------|-----------
Enable1   | 1       | 1          | 0
Enable2   | 1       | 1          | 0
Enable3   | 1       | 1          | 0
Output #1 | 1       | 14         | 0

## Motor Tunings:

Motor tuning will depend on the micro-step mode, as well as the stereotaxic instrument's lead screw.

"Steps per" defines the steps per unit. To make g-codes easy to read and create, 1 unit should equal one millimeter.

"Steps per" Should equal ```micro-steps * steps/rotation * rotations/mm```

For the Kopf Ultra Precise 962 with 1 rotation/mm, with 16 micro-steps and 200 step/rotation motors, this value should be 3200.

Velocity should be approximately 125 units/mm, and acceleration should be 75 units/sec/sec.
