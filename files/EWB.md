# EWB - <ins>E</ins>asy<ins>W</ins>orship <ins>B</ins>ible Text

## Old Format

### Header

| Offset (from begin block) | Length (in bytes) | Type | Description |
| - | - | - | - |
| 0x00 | 22 | String (22 bytes) | Magic: `EasyWorship Bible Text` |
| 0x16 | 10 | Byte[] | Unknown |
| 0x20 | 56 | String (56 bytes) | Language? |

### Book

| Offset (from begin block) | Length (in bytes) | Type | Description |
| - | - | - | - |
| 0x00 | 48 | String (48 bytes) | Name of the book |
| 0x30 | 4 | INT32BE | Amount of chapters |
| 0x34 | 156 | Byte[] | Array of amount of verses inside chapter |
| 0xD0 | 8 | INT64LE | Offset of book in bytes |
| 0xD8 | 8 | INT64LE | Length of book in bytes |

### Compressed name

| Offset (from begin block) | Length (in bytes) | Type | Description |
| - | - | - | - |
| 0x00 | 4 | INT32LE | Length of compressed name |
| 0x04 | (see above) | ZLib Byte[] | Compressed data of name |
