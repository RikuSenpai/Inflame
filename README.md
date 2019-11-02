# Inflame ![](https://img.shields.io/badge/language-Assembly-%236E4C13.svg) ![](https://img.shields.io/badge/assembler-FASM-lightgrey.svg) ![](https://img.shields.io/badge/fasm-1.73.04-orange.svg) ![](https://img.shields.io/badge/platform-Windows-0078d7.svg) ![](https://img.shields.io/badge/arch-x86-yellow.svg) ![](https://img.shields.io/badge/arch-x86--64-red.svg) ![](https://img.shields.io/badge/license-MIT-blue.svg)

User-mode Windows DLL injector written in Assembly language ([FASM](https://flatassembler.net) syntax) with [WinAPI](https://docs.microsoft.com/en-us/windows/desktop/apiindex/windows-api-list).

## Features

- **minimal size:** weighing `1536B` and `2560B`, `32-bit` and `64-bit` version respectively, Inflame is a tiny little injector
- **lightning fast:** injection takes less than `1ms`
- **easy to use:** invoked with Command Line options
- **universal:** both `32-bit` and `64-bit` versions are **actively** maintained
- **safe:** Inflame is **safe to use** and it won't harm your PC. If you don't believe - check the [source code](https://github.com/danielkrupinski/Inflame/tree/master/src).

## Getting Started

### Prerequisites

FASM (flat assembler) for Windows is required to compile Inflame. You can get the latest version [here](https://flatassembler.net/download.php).

Visual Studio is required to compile **manual-map** module - `Inflame.dll` / `Inflame64.dll`. You can omit installing VS by downloading required DLL from Release section.


### Clone

Clone this repo to your local machine
```
git clone https://github.com/danielkrupinski/Inflame.git
```

### Installing

Inflame is available in 2 versions:

* `32-bit` - `Inflame.asm` - for both 32-bit dll and target process
* `64-bit` - `Inflame64.asm` - for both 64-bit dll and target process

1. Choose correct Inflame version based on dll and process architecture. See above.
2. Copy chosen `.asm` file to same directory as `FASM.EXE`.
3. Open cmd.exe there and enter following command:
```
fasm Inflame.asm
```
![](http://g.recordit.co/H6Hy7QYMFA.gif)

or

```
fasm Inflame64.asm
```
![](http://g.recordit.co/zyqawO6UO8.gif)

4. If everything went right you should see output similar to this one:
```
flat assembler  version 1.73.04  (1048576 kilobytes memory)
3 passes, 1536 bytes.
```
and output executable `Inflame.exe` or `Inflame64.exe` should exist.

5. Then switch to `manual-map` branch and open `Inflame.sln` in Visual Studio 2017.

Compile `Inflame.dll` with `x86 | Release`  or `x64 | Release` configuration.

Finally, copy `Inflame.dll` to same directory as `Inflame.exe`.

### Usage

Run `Inflame.exe`/`Inflame64.exe` using following syntax:
```
Inflame / Inflame64 [injection method - see below] [path to dll or dll name when in the same folder] [process name]
```

Available injection method options:

* `-loadlibrary` - LoadLibraryA method
* `-manual-map` - manual map method with thread hijacking

Valid command should look like these:
```
Inflame -loadlibrary test.dll Steam.exe
```
or
```
Inflame64 -manual-map test64.dll notepad.exe
```

## Acknowledgments

* [Zer0Mem0ry](https://github.com/Zer0Mem0ry) for manual map dll injection in C++, available [here](https://github.com/Zer0Mem0ry/ManualMap).
* [Microsoft](https://github.com/Microsoft) for creating beloved Windows API.

## License

> Copyright (c) 2018-2019 Daniel Krupiński

This project is licensed under the [MIT License](https://opensource.org/licenses/mit-license.php) - see the [LICENSE](LICENSE) file for details.
