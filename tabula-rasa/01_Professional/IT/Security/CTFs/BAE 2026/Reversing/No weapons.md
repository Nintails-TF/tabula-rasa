---
date created: Saturday, February 14th 2026, 6:18:25 pm
date modified: Saturday, February 14th 2026, 7:13:29 pm
---

# No Weapons:

**Points:** 300pts
**Description:** N/A
**File:** The `re003_4dba45493eb708b6816bb0df465a3e1f.exe` (PE32 executable for MS windows 5.01 (console), Intel i386)

# Method:
## Description & Investigation:

Firstly, we run `strings`:
```Bash
strings re003_4dba45493eb708b6816bb0df465a3e1f.exe 

...SNIP..
MSVCR100.dll # Tells us that this is Visual C++ 2010
asInvoker # Not admin priviledges
...SNIP..
```

We can now move to using **IDA Free** to disassemble the file.
## Extraction & Discovery:

After opening IDA free, we can locate the functions and decompile the `_wmain` file, using the cloud computing via `F5`:

This gives us the following program:
```C++
int wmain()
{
  FILE *v0; // eax
  unsigned int i; // [esp+0h] [ebp-408h]
  _BYTE *v3; // [esp+4h] [ebp-404h]
  char Buffer[1024]; // [esp+8h] [ebp-400h] BYREF

  for ( i = 0; i < 0x19; ++i )
    Str2[i] ^= 0xAAu;
  printf("Enter password:\n");
  v0 = _iob_func();
  fgets(Buffer, 1024, v0);
  v3 = (_BYTE *)sub_4010E0(Buffer, 10);
  if ( v3 )
    *v3 = 0;
  if ( !strcmp(Buffer, Str2) )
    printf("Bravo!\n");
  else
    printf("Nope.\n");
  return 0;
}
```

We can then click on `Str2` within IDE free, which brings us to the space in the code that has the bytes for the password:

```bytes
.data:00403020 Str2            db 0E3h                 ; DATA XREF: _wmain+33↑r
.data:00403020                                         ; _wmain+46↑w ...
.data:00403021                 db 0DEh
.data:00403022                 db  8Dh
.data:00403023                 db 0D9h
.data:00403024                 db  8Ah
.data:00403025                 db 0CBh
.data:00403026                 db 0C6h
.data:00403027                 db 0C6h
.data:00403028                 db  8Ah
.data:00403029                 db 0C0h
.data:0040302A                 db 0DFh
.data:0040302B                 db 0D9h
.data:0040302C                 db 0DEh
.data:0040302D                 db  8Ah
.data:0040302E                 db 0CFh
.data:0040302F                 db 0C6h
.data:00403030                 db 0CFh
.data:00403031                 db 0C9h
.data:00403032                 db 0DEh
.data:00403033                 db 0D8h
.data:00403034                 db 0C5h
.data:00403035                 db 0C4h
.data:00403036                 db 0D9h
.data:00403037                 db  84h
.data:00403038                 db 0AAh
.data:00403039                 db    0
.data:0040303A                 db    0
.data:0040303B                 db    0
.data:0040303C                 db    0
.data:0040303D                 db    0
.data:0040303E                 db    0
.data:0040303F                 db    0
```

Then you can XOR the bytes using the 0xAA key:
```python
#!/usr/bin/env python3

# XOR-encoded bytes from .data section (Str2 at 0x00403020)
encoded = [
    0xE3, 0xDE, 0x8D, 0xD9, 0x8A, 0xCB, 0xC6, 0xC6,
    0x8A, 0xC0, 0xDF, 0xD9, 0xDE, 0x8A, 0xCF, 0xC6,
    0xCF, 0xC9, 0xDE, 0xD8, 0xC5, 0xC4, 0xD9, 0x84,
    0xAA
]

key = 0xAA

decoded = ''.join(chr(b ^ key) for b in encoded)
print(f"Password: {decoded}")
```

```python
python no-weapons-decode.py 
Password: "It's all just electrons."
```

## Key Takeaways & Remediation:
- IDA Free/Pro is a very overwhelming tool. I feel like a chimpanzee operating a nuclear reactor.
- I'm not too familiar with XOR's quite yet.