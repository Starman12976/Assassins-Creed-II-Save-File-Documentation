
# **File Header**

---

The Assassin's Creed II save file header appears at the very beginning of each save file. It directly precedes the file's body and root container.

## **Structure**

The file header contains these fields in this order:

* Header length - 4-byte unsigned integer representing the header length. Always `24 02 00 00`. The value does not count the field itself or the terminator.
* 4 bytes of padding
* 32-byte checksum - sometimes all ``00``, doesn't appear to be used
* Save file identifer - 12 byte ASCII. Looks like `A C I I   0 `. The number represents which slot the file appears in - `0` for slot 1, `1` for slot 2, and `2` for slot 3. The shared settings file uses `1`.
* 500 bytes of padding
* Standard terminator (`11 00 00 00`)

## **Example**

Below is a standard save file header with each field separated.

```
24 02 00 00|00 00 00 00|63 35 63 30 66 34 66 36
66 30 30 34 33 63 66 65 33 39 30 61 64 30 35 34
32 36 61 34 39 62 65 38|41 00 43 00 49 00 49 00
20 00 30 00|00 00 00 00 00 00 00 00 00 00 00 00 ... 500 total empty bytes
00 00 00 00 00 00 00 00|11 00 00 00
```


