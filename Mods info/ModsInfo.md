For a mod to be viable, it needs to be in a folder inside the "Mods" folder. If the "Mods" does not exists, create it. The name of the mod is the name of the folder in which is in. How should the folders look:

    >Mystery Villa (game folder)
        >Mods
            >mod 1
                >mod 1 files 1
                >mod 1 files 2
                > ...
            >mod 2
                >mod 2 files 1
                >mod 2 files 2
                > ...

You can find some mods examples inside the "Mod examples"
    
What you can't do at the moment:
* create complex animations. only simple "slideshows" that fade in/out. Example is the shower scene with Velma
* create new characters. At the moment you can change the "Stranger" character to have different bodies. It will have all the small animation, and you can add new clothing though outfit mechanic, but you can't open the editor for this character without changing the other that use the "Stranger" character
* create new mini games.

If an original file contains a list of things (eg: store files or clothing/misc files for characters), the data from your files will be added at the end of the already existing files. Otherwise it will overwrite (eg: dialogue files or outfit files)

To add mods for the android build, you need a computer. The mods folder needs to pe places inside the folder:

    Internal storage\Android\data\com.BlobProduction.MysteryVilla\files