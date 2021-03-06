# This 2 That
---
This2that is a universal file converter generator. By writing the proper files for input and output, 
you can instantly add a file format to convert from or to any of the existing supported formats.

## Why?
In the recent past, I've had to google for several file converters. Some were easy to find. Some I never found.
I had this idea. What if there was one file converter, where I can convert any supported format to any other.
This proved to be difficult. Too dificult to achieve. Instead, what if I could write input and output functions
for any given format, and then on demand, link them together? I could create any converter my heart desires with a simple `ld` command.
Another benefit of this approach is this creates a simple and small binary. It can be distributed easily. It will run faster and lighter because
it knows what formats it needs to support.

## How?
By using Flex and Bison, you can quickly create a parser for any structured (not entirely random) format.
The output format will be produced using a set of functions.
These functions have specific names, so that any format can be chosen and linked.
This means that by writing three files, you can support any format you need.
If you only need to convert one way, then you only need to write those files.

1. Compile the input flex and bison files into an object file.
This can be used in step 3 with any other (compatible) format.
2. Compile the output format using the appropriate compiler (C/C++/some other compiled language) into an object file.
3. link the object files produced into an executable.

Note: a script to automate this process is in the works.

## NON-Guarentees
This projects does NOT guarentee any of the following:
- output files will be valid and error free
- output files will match your expectations or be suitable for your needs
- All valid input files will be parsed succesfully
- Invalid input files will fail to parse. (Some may parse entirely despite syntax errors)
- Any desired converter will compile correctly. (Linker errors will probably be common.)
- The format you desire is supported. (It's OSS. If I havent written it, you can.)
- This will compile for you. (developed with: GNU/LINUX 4.9.17 -- GCC 4.8.4)
- This project works at all.

 Of course, I'm doing my best to meet these points, but I cannot/will not promise anything.
 This is provided "AS-IS". Pull requests welcome.

## Notes And Disclaimers
- Current file formats supported (only INI and JSON at time of writing) are processed line by line and maintain little state.
This can limit certain features or prevent a format from processing properly. Future versions will attempt to address this.

- There is a right way to do everything, full of error checking and only using standard libs. This is not that.
This project uses lots of cheats which may not translate to every system, including printing backspaces
for formatting, rather than actually good formatting practices, and using certain functions which may be compiler (gcc) or system specific.
For the most part, this shouldn't affect most people if anyone, but if you're using an unusual or stripped down enviroment, you have been warned.

- Converting flat files (lacking heirarchy. eg. INI or CSV) to those that have multiple levels (JSON or XML) is simple and intuitive,
but going in the opposite direction is tricky if not impossible. I intend to suport such conversions (or try at least),
but make no promises on the resulting file, its usability, or anything else.

## Future Intentions
Eventually, I intend to write parsers for many different types of formats (structured data/audio/video/PE/ELF/etc.).
Each of these formats will have different needs for handling and therefore different functions. While this is intended to be a "universal file converter",
less obvious and possibly nonsensical conversions (JSON to MP3) may not link properly due to a function mismatch.
If you need/desire such conversions then:

1. define what the resulting output file looks like given an input file.
2. write functions appropriately.

If you would like help with that, I would be willing to assist. 
But this project is still very young and lacks many basic formats to begin with.
