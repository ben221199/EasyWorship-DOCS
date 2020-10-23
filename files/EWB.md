# EWB - <ins>E</ins>asy<ins>W</ins>orship <ins>B</ins>ible Text

## Old Format

### Header

**Offset:** 0x00

32 bytes, where the first are forming `EasyWorship Bible Text`.

### Name

**Offset:** 0x20

56 bytes, where it starts with the name and the rest are 0x00.

### Book

**Offset:** 0x58

224 bytes.

| Offset (from begin block) | Length (in bytes) | Type | Description |
| - | - | - | - |
| 0x00 | 48 | String (48 bytes) | Name of the book |
| 0x30 | 4 | INT32BE | Amount of chapters |
| ... | ... | ... | ... |
