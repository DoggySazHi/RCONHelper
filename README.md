# RCONHelper
An RCON client written in C++ with C# interop capabilities.

Written originally for UNObot on Linux clients to send and receive RCON messsages.

## Status
This project is mostly in a stable state; no changes will be made other than possible bugs I encounter during the development of UNObot.

This is built (as far as I know) to the standards indicated at https://developer.valvesoftware.com/wiki/Source_RCON_Protocol.

## Usage
RCONHelper comes with a CMake file for both RCONHelper (the library) and RCONHelper_Test (a Minecraft video player).

To build with sound support, compile with https://github.com/craigsapp/midifile, then modify the CMake file appropriately.

## Contribution
For all problems, please place them in issues. PRs are welcome, though I'm not sure how to handle them.

## License
*Blah blah* [MIT](https://choosealicense.com/licenses/mit/) license. Don't sue me.

```
MIT License

Copyright (c) 2021 William Le

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
