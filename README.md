Josiah Neuberger, josiahneuberger

I have updated this to accept a pixel dimension input on page area export so you can export your assets to any size you want.
I changed the scaling from dpi to Android's scaling factors:

mdpi (x1), hdpi (x1.5), xhdpi (x2), xxhdpi(x3), xxxhdpi (x4)

It's really easy now to add your own customization for your app:

In the file android_export.inx at line 20 - 24 you will find:

***************
	<param name="resdir" type="string" _gui-text="Android Resource directory"></param>
	<param name="size" type="int" min="1" max="1000000" _gui-text="Export square dim. size in pixels">50</param>
	<param name="mdpi" type="boolean" _gui-text="Export MDPI variants">true</param>
	<param name="hdpi" type="boolean" _gui-text="Export HDPI variants">true</param>
	<param name="xhdpi" type="boolean" _gui-text="Export XHDPI variants">true</param>
	<param name="xxhdpi" type="boolean" _gui-text="Export XXHDPI variants">true</param>
	<param name="xxxhdpi" type="boolean" _gui-text="Export XXXHDPI variants">true</param>
	<param name="sw720dp-port" type="boolean" _gui-text="Export sw720dp-port variants">true</param>
***************

As you can see, I added a layout that supports sw720dp-port (smallest width 720dp in portrait mode) (ie. Samsung Galaxy Note 10.1 2012).

Now in the file android_export.py at line 112-117 you will find:

**************
group.add_density_option("mdpi", 1.0)
group.add_density_option("hdpi", 1.5)
group.add_density_option("xhdpi", 2.0)
group.add_density_option("xxhdpi", 3.0)
group.add_density_option("xxxhdpi", 4.0)
group.add_density_option("sw720dp-port", 2.0)
**************

The last line shows you that I want my assets for the new layout sw720dp-port to be 2 times the size of the mdpi asset, which I specify on export of the page area tab.

NOTE:
On windows, the extensions is installed in the programs directory where inkscape is installed under ->share->extensions.

******************************
Original Readme follows...

inkscape-android-export
========

This Inkscape extension exports all selected items in different densities. The exported PNGs will be named by their ID in the SVG.

Install
--------

Download `android_export.inx` and `android_export.py` and copy both files to your `$HOME/.config/inkscape/extensions` folder. A restart of Inkscape is required.

Usage
--------

* Select at least one item to export
* Select `Extensions -> Export -> Android Export…`
* Customize the settings according to your needs

License
========

    Copyright 2013 Christian Becker

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
