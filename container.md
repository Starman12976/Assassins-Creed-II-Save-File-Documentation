
# **Container**

---

Containers are one of the four primary structures in the AC II save file structure. They contain various different types of other elements.

## Structure

Containers have a short header with size data, followed by a list of elements:

* ID - Standard 4-byte ID for this container
* Container Size - The size of the entire container, not including this field.
* Children size - The size of all children in this container. Always the same as the container size - 8
* Children - List of other elements in succession. Can be a record, composite, or array
* End flag - Four bytes, all `00`, signifying the end of the container

## Example

Below is a standard example of a small container that has two records:

```
                     ...(previous element)1E 46
E7 47|32 00 00 00|2A 00 00 00|11 00 00 00 EF 46
78 AF 00 00 00 00 00 00 11 00 0B 00 00 00 00 11
00 00 00 CB F6 C4 90 00 00 00 00 00 00 07 00 0B
77 06 00 00|00 00 00 00(next element)...
```
