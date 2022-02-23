# LMScreen server

###General info:
This is small server to acquire image from Tine and to do simple analysis of picture

The server is better to use with the CameraViewer utility.

###Properties:
Beamline: name of the beamline: P01, P02, P03, P04, P05, P06, P07, P08, P09, P10, P11, P12, P13, P14, P21a, P21b, P22, P23, P24, P25, P61, P62, P63, P64, P65, P66

Screen: LM Screen number: 1, 2, etc. 

List of accessible screens is here

Flip_V: If 1- image will be flipped vertically

Flip_H: If 1- image will be flipped horizontally

Rotate: define the rotation angle in 90 deg steps (!!). E.g. Rotate_Angle = 3 means 270 deg rotation

###Operation:
The analysis is performed in the rectangle, defined by roi_x, roi_y, roi_w, roi_h attributes. In case if the roi_w, roi_h are 0 - the whole picture is analyzed.

The following parameters are calculated:

sum - sum of intensities 
max_intensity - the maximum value
max_x, max_y - position of center of mass
com_x, com_y - position of center of mass
fwhm_x, fwhm_y - horizontal and vertical size of half maximum of peak
Connection to Sardana:
The server has a variable "value" attribute, which can act as a source for the Sardana scans.

The parameter, which should be passed to "value", selected by "scan_parameter" attribute. It could be: "max_i", "max_x", "max_y", "com_x", "com_y", "fwhm_x", "fwhm_y", "sum"

This is the example of entry to the online.xml, to add server to nxselector :

```
<device>
<name>lm4_value</name>
<type>counter</type>
<module>tangoattributectctrl</module>
<device>p23/lmscreen/lm4/value</device>
<control>tango</control>
<hostname>hasep23oh:10000</hostname>
</device>
```

### List of accessible screens (on 22.02.2022):

-------------------------------------------------
| Beamline | Full access | Only frame | No access|
|----------|-------------|------------|----------|
|P01 | LM0  LM1 | | |
|P02 | LM0  LM1 | | |
|P03 | | | LM0  LM1 | 
|P04 | LM0  LM1 | | |
|P05 | LM0  LM1 | | |
|P06 | LM0  LM1 | | |
|P07 | LM0  LM1 | | |
|P08 | LM0  LM1 | | |
|P09 | LM1 | | LM0  |
|P10 | LM0  LM1 LM2 LM3 LM4 | | LM5|
|P11 | LM0  LM1 LM2 LM3 | | | 
|P12 | | | LM0  LM1 |
|P13 | LM0  LM1 | | |
|P14 | LM0  LM1 | | |
|P21a | LM0  LM1 LM3 LM3 LM5 | | LM4 |
|P21b | LM0  LM1 LM3 LM3 LM5 | | LM4 LM6 |
|P22 | LM0 LM1 LM2 LM3 LM4 LM5 LM6 LM7 LM8 LM9 | | |
|P23 | LM0 LM1 LM2 LM3 LM4 LM5 LM6 LM7 LM8 | | |
|P24 | LM0 LM1 LM2 LM3 | LM6 | LM4 LM5 LM7 LM8 LM9|
|P25 | LM0 | | |
|P61 | LM0 LM2 LM3 LM4 LM5 LM6 LM7 LM8 | | LM1 LM9 |
|P62 | LM0 LM1 LM2 LM3 LM4 LM5 LM6 LM7 LM8 LM9 LM10 | | |
|P63 | LM0 LM1 LM3 | | LM2|
|P64 | LM0 LM1 LM2 LM3 LM4 LM5 LM6 LM7 | | |
|P65 | LM0 LM1 LM2 LM3 LM4 LM6 LM7 | | LM5 |
|P66 | | | LM0 |
|----------|-------------|------------|----------|