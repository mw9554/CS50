# Questions

## What's `stdint.h`?

stdint.h is a header file in the C standard library, declare sets of integer types having specified widths, and shall define corresponding sets of macros. 
      It shall also define macros that specify limits of integer types corresponding to types defined in other standard headers.

## What's the point of using `uint8_t`, `uint32_t`, `int32_t`, and `uint16_t` in a program?

      It makes clear that you intend to use the data a specific way.uint24_t means an integer that is exactly 24 bits wide.

## How many bytes is a `BYTE`, a `DWORD`, a `LONG`, and a `WORD`, respectively?
(assume 32-bit architecture like the cs50 appliance)
      BYTE=1byte;
      bit = ...1 bit...
      nybble = 4 bits = 1/2 byte
      byte = 8 bits = 2 nybbles
      WORD = 2 bytes = 4 nybbles = 16 bits
      DWORD = 2 WORDs = 4 bytes = 8 nybbles = 32 bits
      QWORD = 2 DWORDs = 4 WORDS = ..... = 64 bits

## What (in ASCII, decimal, or hexadecimal) must the first two bytes of any BMP file be? Leading bytes used to identify file formats (with high probability) are generally called "magic numbers."

      The header field used to identify the BMP and DIB file is 0x42 0x4D in hexadecimal, same as BM in ASCII

## What's the difference between `bfSize` and `biSize`?

    biSize > The number of bytes required by the structure. (what is the structure exactly ?)

    The structure is the struct BITMAPINFOHEADER. That is a fixed value.
      
    biSizeImage > The size, in bytes, of the image. bfSize > The size, in bytes, of the bitmap file. (what is the difference between image & bitmap file ?)

    biSizeImage is the whole image size, bfSize is the same, but you have to add the size of the 2 header files.

## What does it mean if `biHeight` is negative?

    If biHeight is positive, the bitmap is a bottom-up DIB (device-independent bitmap)
	and its origin is the lower left corner.
	
	If biHeight is negative, the bitmap is a top-down DIB (device-independent bitmap)
	and its origin is the upper left corner.

## What field in `BITMAPINFOHEADER` specifies the BMP's color depth (i.e., bits per pixel)?

    The biBitCount member of the BITMAPINFOHEADER structure determines the number of
	bits that define each pixel and the maximum number of colors in the bitmap.

## Why might `fopen` return `NULL` in lines 24 and 32 of `copy.c`?

    line 24:fopen will return NULL if it cannot find the infile to read in.
    line 32:fopen will return NULL if it cannot create the outfile to write to.

## Why is the third argument to `fread` always `1` in our code?

    I think it is because the program is reading in 1 RGB triple at a time.

## What value does line 63 of `copy.c` assign to `padding` if `bi.biWidth` is `3`?

    biWidth is the width of the bitmap in pixels. If the width is 3, padding is necessary since
	the scanline must be a multiple of 4.
	3 pixels * 3 bytes per pixel = 9 bytes. 3 bytes are added to bring the scanline to 12 bytes.

## What does `fseek` do?

    Skips over any padding and looks for the next pixel (RGB triple)

## What is `SEEK_CUR`?

    This is an integer constant which, when used as the whence argument to the fseek or fseeko function,
	specifies that the offset provided is relative to the current file position

