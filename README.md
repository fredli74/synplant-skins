Synplant V2.0 Skinning Guide
==============================

Synplant version 2.0 supports alternative user interfaces, so-called "skins". A Synplant skin is a folder on disk containing resource files that replace built-in resources. Resource files are images and color choices for the toolbar at the top of the window. It is not possible to change the positions or dimensions of the controls, only their graphical design.

Do not include factory images in your skin. If any resource file is missing in your skin folder, the built-in resource will be used instead. 

Users will use a Synplant script called SkinChooser to select a skin of their liking. The script is included in our offial script package which is available for download at https://soniccharge.com/download.

Skins should be placed in a folder called `Synplant Skins` next to the scripts folder, under the same path as above.

Tip: right-click the SkinChooser window to open a menu where you can refresh the skin choices and easily access the skins folder.

Skin Previews
-------------
<p align="center">
  <img src="Synplant%20Skins/Orchard/thumbnail.png" alt="Orchard" width="200" />
  <img src="Synplant%20Skins/Greyone/thumbnail.png" alt="Greyone" width="200" />
  <img src="Synplant%20Skins/Nightshift/Nightshift.png" alt="Nightshift" width="200" />
  <img src="Synplant%20Skins/factory/factory.png" alt="Factory" width="200" />
</p>



Image formats
-------------
All image resources must be in PNG-8 (index palette), PNG-24 (RGB), or PNG-32 (RGBA) format.

Image dimensions are hardcoded into Synplant and must remain the same.

For animations or multi-state images, we use either frame strips or something we call pixel strips. 

Frame strips are images where each frame is stacked vertically. For example, a 100x100 pixel button animation with eight frames would be represented by a 100x800 pixel image.

Pixel strips are a proprietary format that can be used on large animations to save space. In a pixel strip, each pixel from each frame is sequenced horizontally. By rearranging pixels this way it is usually possible to achieve a much higher degree of file compression. We have a simple command-line utility to convert between frame strips and pixel strips that can be [downloaded here](https://github.com/fredli74/pixelSequencer/releases/latest).

Image Specifications
--------------------
```
arcslider_x2.png            704 x 96       (  88 x 96  * 8 frames )
btndna_x2.png               104 x 416      ( 104 x 104 * 4 frames )
btngeno_x2.png              104 x 416      ( 104 x 104 * 4 frames )
btnmenu_x2.png              104 x 208      ( 104 x 104 * 2 frames )
btnnext_x2.png               56 x 240      (  56 x 80  * 3 frames )
btnprev_x2.png               56 x 240      (  56 x 80  * 3 frames )
btnredo_x2.png              104 x 312      ( 104 x 104 * 3 frames )
btnsave_x2.png              104 x 416      ( 104 x 104 * 4 frames )
btnundo_x2.png              104 x 312      ( 104 x 104 * 3 frames )
faceplate_x2.png           1000 x 1400
keyringbuttons_x2.png       744 x 9312     ( 744 x 776 * 12 frames )
layerbuttons_x2.png         744 x 9312     ( 744 x 776 * 12 frames )
layerglow_x2.png            744 x 8928     ( 744 x 744 * 12 frames )
layerlights_x2.png          744 x 8928     ( 744 x 744 * 12 frames )
layerring_x2.png            744 x 744
patchdisplay_x2.png         456 x 64
patchspecular_x2.png        456 x 64
seed_x2.png                  56 x 56
sliderleft_x2.png            96 x 72
slidermid_x2.png             96 x 72
sliderright_x2.png          104 x 72
smalldisplay_x2.png         216 x 48
switchmode_x2.png           248 x 288      ( 248 x 72 * 4 frames )
```

Skin Config File
----------------
Each skin has a corresponding `.scskin` config text-file in the following format.
```
SynplantSkin: {
    format: 1                         // Synplant skin format.
    name: "My Awesome Skin"           // Visible to end user.
    version: "1.0"                    // Visible to end user.
    by: "Fredrik Lidstr\xf6m"         // Visible to end user.
    url: "https://soniccharge.com"    // Optional (i) url.
    thumbnail: "Awesome"              // Name of PNG image (full resolution: 1000x1400)
}
```
Use ISO-8859-1 encoding for strings with C-style escaping.


Color Scheme File
-----------------
Synplant2_colorScheme.makaron contains color definitions for the vector graphics elements.
```
@define STAYUPMENU_FRAME_COLOR = #2f3c49
@define STAYUPMENU_BACKGROUND_COLOR = #141b22
@define STAYUPMENU_BACKGROUND_SELECTED_COLOR = #233951
@define STAYUPMENU_TEXT_COLOR = #77777f
@define STAYUPMENU_TEXT_SELECTED_COLOR = #888898
```
Colors can be expressed in a few different ways:
```
#rrggbb        // hex RGB
#aarrggbb      // hex RGB with "premultiplied" alpha
rgb(r,g,b)     // decimal RGB (between 0.0 and 1.0)
rgb(r,g,b,a)   // decimal RGB + alpha (no premultiply)
hsv(h,s,v)     // hue saturation value
hsv(h,s,v,a)   // hue saturation value + alpha
```


Contributing
------------
Please follow standard GitHub procedures for contributing or updating your skin.
* Create a personal fork of this project.
* In your fork, create a new branch to work on.
* Add your skin in a new folder under `Synplant Skins`.
* From your fork, open a pull request in the correct branch into this repository.
