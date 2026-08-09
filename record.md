
# **Record**

---

Records are the simplest element of the Assassin's Creed II file system. They act as leaf nodes in its container structure. They hold a single piece of data within them and are typically clustered together in big groups within a larger container.

## **Structure**

Every record has five parts: A primary ID, a secondary ID, a type flag, a payload, and a terminator. Shown below is an example record of where the Florin count is stored, with each part labeled:

> **Florins Value Record:** `12 99 7B F7 | 00 00 00 00 00 00 00 | 07 00 0B | 20 A1 07 00 | 11 00 00 00`

- `12 99 7B F7` - Primary ID. In this case, it is a "value" ID
- `00 00 00 00 00 00` - Secondary ID. In most records, this is all 0, but not always
- `07 00 0B` - Type flag. This one means "unsigned integer". All type flags end with `0B`
- `20 A1 07 00` - Payload. This value is 500,000 florins in little-endian
- `11 00 00 00` - Standard terminator. `11 00 00 00` is the most common type, signifying that this is not the last record in the parent container

#### Below are a few more examples:

> * **Synchronization Record:** `2B 13 F5 28 | 00 00 00 00 00 00 | 07 00 0B | 64 00 00 00 | 11 00 00 00`
> * **Save Photo Record:** `C2 FC 11 71 | 47 3E B6 FB 00 00 | 12 00 0B | DC 59 B6 48 | 11 00 00 00`
> * **Timestamp Record:** `1B 19 00 8C | 00 00 00 00 00 00 | 07 00 0B | A6 30 70 6A | 12 00 00 00`

## **Type Flags**

Below is a list of all recorded type flags, along with a description if it is known:

> * `07 00 0B` - Likely unsigned integer, 4-bytes
> * `19 00 0B` - Appears to be used for a 4-byte integer + some 4-byte hash.
> * `1D 0A 0B` - Flag byte (`1` or `0`) + 4-byte unsigned integer
> * `03 00 0B` - Uncertain. Appears to always be between 3584-3587
> * `12 00 0B` - Used for 4-byte location codes
> * `00 00 0B` - 1-byte boolean value
> * `1A 00 0B` - Length-prefixed ASCII string. Only used for the save file name

