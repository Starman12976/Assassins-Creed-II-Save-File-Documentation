
# Array

---

Arrays are one of the four primary structures in the AC II file structure. They contain consecutive 4-byte entries that represents various collectible items in the game.

## Structure

An array contains the following fields:

* Size - The byte size of the array, not including this element
* Primary ID - Standard primary ID for this array
* Secondary ID - Standard secondary ID for this array
* Tag - Data type tag
* Flag - Unknown byte flag
* Count - Integer with the number of array elements
* Values - List of values, each 4 bytes

## Example

Below is an example of a small 9-element array

```
(prev)36 00 00 00|42 76 31 53|00 00 00 00 00 00|
9D 03 0B|01|09 00 00 00|1E 00 00 00 64 00 00 00
08 00 00 00 06 00 00 00 14 00 00 00 1E 00 00 00
CA 01 00 00 0E 00 00 00 00 00 00 00 (next)...
```
