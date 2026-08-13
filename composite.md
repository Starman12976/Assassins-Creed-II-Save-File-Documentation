
# Composite

---

Composites are one of the four primary structures in the AC II save file structure. They act like a record and a container together, and all of their children are containers.

## Structure

The composite structure starts like a single record followed by a list of containers. Each field and its description can be found below:

* Size - Size of the record + all children, not including this field itself
* Primary ID - Standard record primary ID
* Secondary ID - Standard record secondary ID
* Tag - Record tag. This is always one of two different types (see below)
* Flag - 1-byte flag, only exists with certain tags
* Count - 4-byte count of the number of children, only exists with certain tags
* Padding - A variable number of padding bytes. This can reliably be skipped by reading until the first byte that is not `00`
* Children - A sequential list of containers

## Tags

Whether or not the composite has a payload depends on its tag. There are only three tags with this behavior: `1D 0A 0B`, `9D 0A 0B`, and `1D 0B 0B`. These have a payload of a byte flag and a 4-byte count signifying the number of children. Any other tag has no payload. The exact meaning of these tags is unknown, and changing the flag byte usually results in a crash.

## Example

Below is an example of a small composite with 1 container:

```
                 ...(previous element) 57 00 00
00|EB 07 8A BA|1E 46 E7 47 00 00|9D 0A 0B|01|01
00 00 00|00 00 00 00 00 00 00 00 00 00 00|1E 46
E7 47 32 00 00 00 2A 00 00 00 11 00 00 00 EF 46
78 AF 00 00 00 00 00 00 11 00 0B 00 00 00 00 11
00 00 00 CB F6 C4 90 00 00 00 00 00 00 07 00 0B
77 06 00 00 00 00 00 00 (next element)...
```
