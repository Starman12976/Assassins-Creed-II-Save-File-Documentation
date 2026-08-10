
# **Body**

---

The save file's body contains the rest of the file data after the header. It contains some file data followed by the root container, the top-level container for all save data.

## **Structure**

The body contains these fields:

* Body ID - Always `AC DB FE 00`
* Unknown constant - Always `1`. The game will crash if it is changed.
* Root container ID - Always `52 3B BE BD`. This is the ID of the game's top-level container.
* Unknown constant - Always `3`. Changing this value appears to do nothing.
* 7 bytes of padding, all `00`
* The game's root container

## **Example**

Below is an example of the file body:

```
                        ...(header)|AC DB FE 00|
01|52 3B BE BD|03|00 00 00 00 00 00 00 00 00 00|
(root container)...

```
