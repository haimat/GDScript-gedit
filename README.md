GDScript-gedit
==============

This is the *GDScript* syntax definition for the gedit text editor.
GDScript is the scripting language for the [Godot Game Engine](http://www.godotengine.org/).

Note that since Gnome's gedit is based on the *gtksourceview* library,
you can use this language spec file for all editors that are based on this library as well.
For example, Xfce's mousepad editor uses gtwsourceview too.

Installation
------------

If you want to install the language spec file for your own user account only, then you first need
to create a new directory under `~/.local/share`, if it does not exist yet:

* `~/.local/share/gtksourceview-2.0/language-specs` (for Gtk2-based editors, e.g. under Xfce)
* `~/.local/share/gtksourceview-3.0/language-specs` (for Gtk3-based editors, e.g. under Gnome)

Afterwards you can copy the `gdscript.lang` file from this repo into the new folder.

For a system-wide installation you need to put the `gdscript.lang` file into the
`/usr/share/gtksourceview-{2|3}.0/language-specs` directory (again depending on your Gtk version).

MIME Type Information
---------------------

After saving the `gdscript.lang` to your machine, as described above, and opening a Godot source
file into your editor, you should already be able to select the GDScript file type from the menu.

To have your editor automatically recognize the GDScript file type, you need to create a MIME Type
for it. For this you need to create a new file `gdscript.xml` with the following content (assuming
your Godot script files end with `.gd`):

    <mime-info xmlns='http://www.freedesktop.org/standards/shared-mime-info'>
      <mime-type type="text/x-gdscript">
        <comment>GDScript Source</comment>
        <glob pattern="*.gd"/>
      </mime-type>
    </mime-info>

To make this new MIME type available for your own user only, save the new file to the following folder:
`~/.local/share/mime/packages`. Or, if you want to install the MIME type system-wide, place the XML file
under `/usr/share/mime/packages`.

In order to let your machine recognize this new MIME type, run the following command on your shell:

`shell$ update-mime-database /path/to/the/xml/file`

where you replace `/path/to/the/xml/file` with the folder name to which you saved the MIME type XML file.
After (re-)starting your editor the GDScript file should be automatically recognized. (Note that you may
need to restart X in order for the changes to take effect.)

Godot Setup
-----------

The last step is to tell Godot to use the text editor of your choice as the source code editor for GDScript
files. In the Godot environment open the *Settings* menu (in the top-right corner) and select *Editor Settings*.
Here scroll down until you find the options category called *External Editor*. Simply enter the path to your
editor executable, for example `/usr/bin/gedit`, and activate the *User External Editor* checkbox.

**Have fun!**
