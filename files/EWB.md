# EWB - <ins>E</ins>asy<ins>W</ins>orship <ins>B</ins>ible Text

## Old Format

### Header

| Offset (from begin block) | Length (in bytes) | Type | Description |
| - | - | - | - |
| 0x00 | 22 | String (22 bytes) | Magic: `EasyWorship Bible Text` |
| 0x16 | 10 | Byte[] | Unknown (`1A 02 3C 00 00 00 E0 00 00 00`), where it is possible that `E0` is part of book block length |
| 0x20 | 56 | String (56 bytes) | Language? |

### Book (66 times)

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
| 0x04 | (see above) | Byte[] (ZLib compressed) | Compressed data of name |

### Compressed data (66 times)

| Offset (from begin block) | Length (in bytes) | Type | Description |
| - | - | - | - |
| 0x00 | variable | Byte[] (ZLib compressed) | Book content |

After all these blocks, you will a same amount of data blocks as the Book blocks earlier.
All these blocks are ZLib compressed.

If you decompress these blocks, you will find plain text.
Every line, ending with `\r\n\r\n`, is one verse of the following format:
```
<line> = <chapter> ":" <verse> <SP> <text> <CRLF> <CRLF>
```

### Footer

| Offset (from begin block) | Length (in bytes) | Type | Description |
| - | - | - | - |
| 0x00 | 8 | Byte[] | Unknown (`18 3A 00 00 00 00 00 00`) |
| 0x08 | 8 | String (8 bytes) | `ezwBible` |

## New format

SQLite
