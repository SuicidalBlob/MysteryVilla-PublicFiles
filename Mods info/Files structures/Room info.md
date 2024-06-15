A modded room has 2 mods: overwrite and add. It you add a room that already exists, it will overwrite the already existing.

In a room folder you can have:
* back - the background image of the room
* objects - a file with the json data of a list of objects inside to room
* <back_variants> - images that can be use for background variants

### Objects
In the "objects" file is the json representation of an array of objects. The structure is:

    Vector2 position
                - the relative position of the object
                - [0, 0] is the low left corner
                - [1, 1] is the upper right corner
    Vector2 size
                - the relative size of the object
                - [1, 1] is the entire screen
    float angle
                - the angle of the object
    Type[] types
                - a list of types the object is:
                    - 0 : an object sprites, part of the background props
                    - 1 : a button
    string propImagePath
                - the object sprite location
    string buttonImagePath
                - the button sprite name
                - current accepted names:
                    - circle
                    - semi_circle1
                    - semi_circle2
                    - semi_circle3
                    - semi_circle4
                    - map
                    - InputFieldBackground
                    - Background
                    - Knob
    float pixelsPerUnitButtonImage = 1
                - used to change the roundness of the button
    string buttonText
                - the text of the button
    bool disconnectText = false
                - if true, the text wil not disappear when the mouse is not hovering over the button
    string buttonType
                - what type of behavior the button should have
                - accepted vales:
                    - OSI_MoveTo
                    - OSI_OpenDialogue
                    - OSI_OpenEditor
                    - OSI_OpenCharacterInfoMenu
    string[] buttonData
                - the data send to the button behavior
    Color color
                - the color of the button
    float notHoverButtonAlpha = 0
                - the alpha multiplayer of the button when the mouse is not over the button
    float hoverButtonAlpha = 1
                - the alpha multiplayer of the button when the mouse is over the button
    string condition
                - condition of the object
                - if false, the object will not be created