[Back to README](README.md)

# Dialogue commands:
    ->any part of command part starts with @<str_sub> will be replace with the string substitute of <str_sub>

        -> if the command part starts with @+<str_sub>, at the previous command part will be added string substitute of <str_sub> and the current part will be removed
    
        -> specials:
            * input -> last user input, empty string by default
* moveTo [room_name] [background_variant_name] [do_not_load_props](only this value)
* dialogue
    * start <dial_name> [continue_from_this_point](any value, multiple values allowed)
        > automatically set temporary arguments: @arg_s<i> for string and $arg_t<i> for equations contained in [continue_from_this_point]
    * restart [continue_from_this_point](any value)
    * speed <line_speed>
    * size <line_size>
    * style <line_style>
    * auto [seconds_until_play_next_line](default 0)
    * character
        * move <name> <vertical_position> [horizontal_position=0] [scale=1] [initial_animation_name]
        * show <name> [new name] <vertical_position> [horizontal_position] [scale] [animation]
        * hide <name>
        * hideAll
        * outfit <name>
            > character to default outfit
        * outfit <name> <outfit_name>
        * outfit <name> removeTag <outfit_tag>
        * lookback <name>
        * emote <name> (face <face_name> | eyes <eyes_name> | mouth <mouth_name> | eyebrows <eyebrows_name> | <other> [opacity])+
            > opacity can be an equation ony if it start with "ec:"
        * wearMisc <name> <misc_name>
        * wearCloth <name> <clothing_name>
        * skinColor <name> <R>,<G>,<B>[,A]
        * skinColor <name> random
        * skinColor <name> last
            > changes color to last random color
        * doNotUseDefaultAppearance <name> -> for using skin color on start of scene
        * setSkinMaterial <name> <type>
            > type from {0, 1, 2}
        * play <animation_name>
        * stopAnimation <animation_name>
* c <name> <command_parts>
    > shortcut for command: dialogue character <command_part> <name> <rest_of_commands_parts>
* outfit <car_name> <command> <name> [C=<color>] [A=<alpha>]
    * command can be: wearCloth, wearMisc, removeTag
* notification <notification_text>
* if <boolean_equation>
* movecharacterto <car_name> <place_name>
* buy <character_name> <item_name>
* setVar <var_name> <_equation>
* setCar <character_name> <var_name> <_equation>
* addCar <character_name> <var_name> <_equation> [min:_equation] [max:_equation]
    > if min or max is set, the old value is inside the value and the new value is outside of the value, the new value will clamp to those values and a temporary variable "$arg_t0" will have the new value of the value added

    > examples (Nan means not set, and any means any values):

    | old value | to add | min | max | value saved  | $arg_t0 |
    | --------- | ------ | --- | --- | ------------ | ------- |
    | 8         | +4     | Nan | Nan | 12           |  4      |
    | 8         | -4     | Nan | Nan |  4           | -4      |
    | 8         | +4     | any | 10  | 10           |  2      |
    | 8         | -4     |  6  | any |  6           | -2      |
    | 8         | +4     | any | 5   |  8           |  0      |
    | 8         | -4     | 10  | any |  8           |  0      |
* setRename <character_name> <rename> <new_rename>
* setStr <string_name> <string_value>
* nextDay
* skip
* HScene
    * start <hscene_name>
    * stop
    * setParameter <param_name> <_equation> [instant](any value)
    * variant <variant_name> [one_variant](any value)
    * play <state_name>
    * sound <sound_name>
    * sound stop <sound_name>
* Minigame
    * start <minigame_name> [arguments]
* book <book_name>
    > open a book to read
* play
    * music [music_name]
    * sfx <sfx_clip_sound_name>
    * stop <sfx_clip_sound_name>
* openInput
* store
    * open <file_name> <display_name> [seller_image]
    * close

# Variable type
* \# -> global variable
* ? -> daily variable; get reset to 0 every day
* $ -> temporary global variable; are not saved in save files
* function

    -> call the function if the string is in format func_name[param1,...]

    -> else call the function with the name = given string and zero parameters

# Functions
* used in equations
* formation: func_name[param1,param2,...]
* functions:
    * isinroom[character_name] -> return 1 if the character is in current room, else return 0
    * character[character_name,val_name] -> return the character's value
    * random -> random [0, 1]
    * random[val] -> random [0, val]
    * random[min,max] -> random [min, max]
    * hastag[character_name,tag_name] -> return the number of items that contains the tag of character's default appearance
    * hascurenttag[character_name,tag_name] -> return the number of items that contains the tag of character's on screen appearance
    * wearitem[character_name,item_name] -> 1 if the character default appearance has item equipped
    * hasitem[character_name,item_name] -> 1 if the character has the item bought
    * int[floating_value] -> return a natural number
    * isinput[string_value] -> return 1 if the last input value was the string_value
    * isinputsensitive[string_value] -> same as isinput but is chase sensitive
    * isstring[string_substitute,string_val] -> return 1 if string_substitute value is the same with string_val (no case sensitive)
    * negative[equation] -> return -1*equation
    * settings[setting_name/fetish] -> return the value of a setting or fetish

# String substitution
* ec:<_equation> | equation:<_equation>
* character:<character_name>,<character_rename>
* m:(* ,<String_substitution>) *

    -> get a string combined with with characters and other string substitutions

    -> replace \b with a space so that it can be the whole string in a single word