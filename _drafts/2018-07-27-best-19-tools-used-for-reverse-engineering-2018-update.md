---
title: Best 19 Tools Used For Reverse Engineering – 2018 Update
author: Mümin Köykıran
date: 2018-07-27 18:32:00 -0500
categories: []
tags: []
---


### **1. Nudge4j**

[Nudge4j](https://lorenzoongithub.github.io/nudge4j/) is a tiny piece of Java code to make your Java application accessible to the browser. It’s meant for use during development to provide an environment for experimenting with code against a running application.

**Github Link –** [https://github.com/lorenzoongithub/nudge4j](https://github.com/lorenzoongithub/nudge4j)

**With nudge4j you can:**

-   Control your Java application from the browser, as if the browser was a smarter remote control.
-   Send code from the browser to run on the JVM,
-   Experiment with live code.

The only requirement to use Nudge4j is Java8 and any compatible latest browser i.e. Firefox/Chrome.

[![](https://i1.wp.com/www.muminkoykiran.com/blog/wp-content/uploads/2018/07/nudge4j.png?resize=597%2C389&ssl=1)](https://i1.wp.com/www.muminkoykiran.com/blog/wp-content/uploads/2018/07/nudge4j.png?ssl=1)

For **Nudge4j Demo**, please visit [nudge4j.appspot.com](http://nudge4j.appspot.com/)

### **2. IDA**

IDA is a multi-processor [disassembler and debugger](https://www.hex-rays.com/products/ida/support/tutorials/index.shtml) that offers so many features and works perfectly on all platforms like Windows, Linux or Mac OS X. IDA has become the de-facto standard for the analysis of hostile code, vulnerability research and COTS validation.

**Website Link –** [https://www.hex-rays.com/products/ida/](https://www.hex-rays.com/products/ida/)

You can easily download [IDA 5.0](https://www.hex-rays.com/products/ida/support/download_freeware.shtml) which is freely available on the website. In 2001, IDA Pro was a finalist in the 18th PC Magazine Awards for Technical Excellence. It was a runner-up to Microsoft .NET architecture.

[![](https://i1.wp.com/www.muminkoykiran.com/blog/wp-content/uploads/2018/07/ida-tool.gif?resize=800%2C600&ssl=1)](https://i1.wp.com/www.muminkoykiran.com/blog/wp-content/uploads/2018/07/ida-tool.gif?ssl=1)

For IDA Evaluation version as a demo, you just need to fill out the small form by clicking [this link](http://out7.hex-rays.com/demo/request). The full version of IDA is not limited in any way, comes with one full year of free e-mail support and one full year of free downloadable upgrades.

### **3. OllyDbg**

OllyDbg is a 32-bit assembler level analysing debugger for Microsoft Windows. Emphasis on binary code analysis makes it particularly useful in cases where source is unavailable. OllyDbg is a shareware, but you can download and use it for free.

**Website Link –** [http://www.ollydbg.de/](http://www.ollydbg.de/)

**Features of OllyDbg –**

-   Intuitive user interface, no cryptical commands
-   Code analysis – traces registers, recognizes procedures, loops, API calls, switches, tables, constants and strings
-   Directly loads and debugs DLLs
-   Object file scanning – locates routines from object files and libraries
-   Allows for user-defined labels, comments and function descriptions
-   Understands debugging information in Borland format
-   Saves patches between sessions, writes them back to executable file and updates fixups
-   Open architecture – many third-party plugins are available
-   No installation – no trash in registry or system directories

[![](https://i1.wp.com/www.muminkoykiran.com/blog/wp-content/uploads/2018/07/ollydbg.png?resize=989%2C727&ssl=1)](https://i1.wp.com/www.muminkoykiran.com/blog/wp-content/uploads/2018/07/ollydbg.png?ssl=1)

For all Reverse Engineering Tutorials, Visit [Tuts4you.com](https://tuts4you.com/e107_plugins/download/download.php?list.17).

### **4. x64dbg**

x64dbg is an open-source x64/x32 debugger for Windows.

**Website Link –** [https://x64dbg.com/#start](https://x64dbg.com/#start)

**Github Link –** [https://github.com/x64dbg/x64dbg](https://github.com/x64dbg/x64dbg)

**Features of X64dbg –**

-   [x64dbg](https://github.com/x64dbg/x64dbg/releases) is under contact active development.
-   It provides both executable and the source through you can also contribute.
-   It can debug both x64 and x32 applications with the help of single interface.
-   x64dbg uses Qt, TitanEngine, capstone, Yara, Scylla, Jansson, lz4, XEDParse, Keystone, asmjit and snowman.
-   x64dbg uses C++ and Qt to quickly add new features.
-   x64dbg has many features thought of or implemented by the reversing community.
-   x64dbg has an integrated, debuggable, ASM-like scripting language.

[![](https://i2.wp.com/www.muminkoykiran.com/blog/wp-content/uploads/2018/07/x64dbg-1024x545.png?resize=1024%2C545&ssl=1)](https://i1.wp.com/www.muminkoykiran.com/blog/wp-content/uploads/2018/07/x64dbg.png?ssl=1)

For compiling the whole project with x64dbg, refer to [wiki guide](https://github.com/x64dbg/x64dbg/wiki/Compiling-the-whole-project).

### **5. dex2jar**

A collection of tools and libraries that can work with Android **.dex** and java **.class** files in order to help programmers to streamline the development process. [**Dex2jar**](http://www.softpedia.com/get/Programming/Other-Programming-Files/dex2jar.shtml) consists of a collection of Java libraries that can streamline development tasks for Android related concepts and can simplify APK projects.

**Github Link –** [https://github.com/pxb1988/dex2jar](https://github.com/pxb1988/dex2jar)

**Sourceforge Link –** [https://sourceforge.net/projects/dex2jar/](https://sourceforge.net/projects/dex2jar/)

**Dex2jar contains following components:**

-   **dex-reader** is designed to read the Dalvik Executable (.dex/.odex) format. It has a light weight API similar with ASM.
-   **dex-translator** is designed to do the convert job. It reads the dex instruction to dex-ir format, after some optimize, convert to ASM format.
-   **dex-ir** used by dex-translator, is designed to represent the dex instruction
-   **dex-tools** tools to work with .class files.
-   **d2j-smali** disassemble dex to smali files and assemble dex from smali files. different implementation to smali/baksmali, same syntax, but we support escape in type desc “Lcom/dex2jar\t\u1234;”
-   **dex-writer** write dex same way as dex-reader.

[![](https://i0.wp.com/www.muminkoykiran.com/blog/wp-content/uploads/2018/07/dex2jar-1024x699.png?resize=1024%2C699&ssl=1)](https://i1.wp.com/www.muminkoykiran.com/blog/wp-content/uploads/2018/07/dex2jar.png?ssl=1)

To use this tool, please use below syntax:

> sh d2j-dex2jar.sh -f ~/path/to/apk_to_decompile.apk

### **6. JD-GUI**

JD-GUI is a standalone graphical utility that displays Java source codes of .class files. You can browse the reconstructed source code with the **JD-GUI** for instant access to methods and fields.

**Website Link –** [http://jd.benow.ca/](http://jd.benow.ca/)

**Github Link –** [https://github.com/java-decompiler/jd-gui](https://github.com/java-decompiler/jd-gui)

The latest version of JD-GUI is 1.4.0 which you can easily download the jar package from [this link](https://github.com/java-decompiler/jd-gui/releases/download/v1.4.0/jd-gui-1.4.0.jar).

[![](https://i0.wp.com/www.muminkoykiran.com/blog/wp-content/uploads/2018/07/jd-gui.png?resize=631%2C402&ssl=1)](https://i0.wp.com/www.muminkoykiran.com/blog/wp-content/uploads/2018/07/jd-gui.png?ssl=1)

**How to launch JD-GUI ?**

-   Double-click on “**jd-gui-x.y.z.jar**“
-   Open a file with menu “**File > Open File…**“
-   Open recent files with menu “**File > Recent Files**“
-   Drag and drop files from your file explorer.

### **7. Procyon**

Procyon is one of the most popular open source Java Decompiler. The Procyon decompiler handles language enhancements from Java 5 and beyond that most other decompilers don’t. It also excels in areas where others fall short.

**Website Link –** [https://bitbucket.org/mstrobel/procyon/wiki/Java%20Decompiler](https://bitbucket.org/mstrobel/procyon/wiki/Java%20Decompiler)

**Procyon in particular does well with:**

-   Enum declarations
-   Enum and String switch statements (only tested against javac 1.7 so far)
-   Local classes (both anonymous and named)
-   Annotations
-   Java 8 Lambdas and method references (i.e., the :: operator).

[![](https://i1.wp.com/www.muminkoykiran.com/blog/wp-content/uploads/2018/07/Procyon-decompiler-1024x389.png?resize=1024%2C389&ssl=1)](https://i1.wp.com/www.muminkoykiran.com/blog/wp-content/uploads/2018/07/Procyon-decompiler.png?ssl=1)

To download **Procyon decompiler**, please visit [https://bitbucket.org/mstrobel/procyon/downloads/](https://bitbucket.org/mstrobel/procyon/downloads/)

### **8. Androguard**

[Androguard](https://code.google.com/archive/p/androguard/) is mainly a tool written in python to play with : * Dex/Odex (Dalvik virtual machine) (.dex) (disassemble, decompilation), * APK (Android application) (.apk), * Android’s binary xml (.xml), * Android Resources (.arsc). It is also available for Linux/OSX/Windows (python powered).

**Github Link –** [https://github.com/androguard/androguard/](https://github.com/androguard/androguard/)

[![](https://i1.wp.com/www.muminkoykiran.com/blog/wp-content/uploads/2018/07/androguard.png?resize=966%2C360&ssl=1)](https://i1.wp.com/www.muminkoykiran.com/blog/wp-content/uploads/2018/07/androguard.png?ssl=1)

**Features of Androguard –**

-   Map and manipulate DEX/ODEX/APK/AXML/ARSC format into full Python objects,
-   Diassemble/Decompilation/Modification of DEX/ODEX/APK format,
-   Decompilation with the first native (directly from dalvik bytecodes to java source codes) dalvik decompiler (DAD),
-   Access to the static analysis of the code (basic blocks, instructions, permissions (with database from http://www.android-permissions.org/) …) and create your own static analysis tool,
-   Analysis a bunch of android apps,
-   Analysis with ipython/Sublime Text Editor,
-   Diffing of android applications,
-   Measure the efficiency of obfuscators (proguard, …),
-   Determine if your application has been pirated (plagiarism/similarities/rip-off indicator),
-   Check if an android application is present in a database (malwares, goodwares ?),
-   Open source database of android malware,
-   Detection of ad/open source librairies (WIP),
-   Risk indicator of malicious application,
-   Reverse engineering of applications (goodwares, malwares),
-   Transform Android’s binary xml (like AndroidManifest.xml) into classic xml,
-   Visualize your application with gephi (gexf format), or with cytoscape (xgmml format), or PNG/DOT output,
-   Integration with external decompilers (JAD+dex2jar/DED/fernflower/jd-gui…)

### **9. DotPeek**

dotPeek is a free-of-charge standalone tool based on ReSharper’s bundled decompiler. It can reliably decompile any .NET assembly into equivalent C# or IL code. This decompiler supports multiple formats including libraries (.dll), executables (.exe), and Windows metadata files (.winmd).

**Website Link –** [https://www.jetbrains.com/decompiler/](https://www.jetbrains.com/decompiler/)

### [![](https://i2.wp.com/www.muminkoykiran.com/blog/wp-content/uploads/2018/07/dotpeek.png?resize=1000%2C684&ssl=1)](https://i2.wp.com/www.muminkoykiran.com/blog/wp-content/uploads/2018/07/dotpeek.png?ssl=1)

**Features of dotPeek –**

-   As soon as you’ve decompiled an assembly, you can save it as a Visual Studio project (.csproj).
-   dotPeek can identify local source code based on PDB files, or fetch source code from source servers such as Microsoft Reference Source Center or SymbolSource.
-   dotPeek inherits a lot of features from ReSharper. These include contextual and context-insensitive navigation, usage search, as well as different code structure and hierarchy views.
-   Whenever you put a caret on a symbol in the code view area, dotPeek offers a plethora of contextual navigation options that are all available via Navigate To drop-down menu.
-   dotPeek indexes all assemblies in your assembly list, as well as all assemblies that they reference, and provides features to quickly jump to specific code. For instance, Go to Everything allows searching for an assembly, namespace, type, member, or a recently opened file.

Getting started with **dotPeek**, visit [dotPeek Documentation](https://www.jetbrains.com/decompiler/documentation/documentation.html).

### **10. ILSpy**

ILSpy is the open-source .NET assembly browser and decompiler. The latest version of ILSpy is 3.0.1 which is just released 10 days ago i.e. on 21st Dec 2017 but ILSpy 3.0 is one of the most stable version ever.

**Github Link –** [https://github.com/icsharpcode/ILSpy/](https://github.com/icsharpcode/ILSpy/)

[![](https://i0.wp.com/www.muminkoykiran.com/blog/wp-content/uploads/2018/07/ILSpy-1024x713.png?resize=1024%2C713&ssl=1)](https://i1.wp.com/www.muminkoykiran.com/blog/wp-content/uploads/2018/07/ILSpy.png?ssl=1)

**Features of ILSpy –**

-   Decompilation to C#
-   Whole-project decompilation (csproj, not sln!)
-   Search for types/methods/properties (substring)
-   Hyperlink-based type/method/property navigation
-   Base/Derived types navigation, history
-   BAML to XAML decompiler
-   Extensible via plugins (MEF)

### **11. DnSpy**

DnSpy is a debugger and .NET assembly editor. You can use it to edit and debug assemblies even if you don’t have any source code available.

**Github Link –** [https://github.com/0xd4d/dnSpy](https://github.com/0xd4d/dnSpy)

[![](https://i0.wp.com/www.muminkoykiran.com/blog/wp-content/uploads/2018/07/dnSpy.png?resize=842%2C632&ssl=1)](https://i0.wp.com/www.muminkoykiran.com/blog/wp-content/uploads/2018/07/dnSpy.png?ssl=1)

**Features of DnSpy –**

-   Debug .NET Framework, .NET Core and Unity game assemblies, no source code required
-   Edit assemblies in C# or Visual Basic or IL, and edit all metadata
-   Light and dark themes
-   Extensible, write your own extension
-   High DPI support (per-monitor DPI aware)
-   And much more…

### **12. De4dot**

de4dot is an open source (GPLv3) .NET deobfuscator and unpacker written in C#. It will try its best to restore a packed and obfuscated assembly to almost the original assembly. Most of the obfuscation can be completely restored (eg. string encryption), but symbol renaming is impossible to restore since the original names aren’t (usually) part of the obfuscated assembly.

**Github Link –** [https://github.com/0xd4d/de4dot](https://github.com/0xd4d/de4dot)

[![](https://i2.wp.com/www.muminkoykiran.com/blog/wp-content/uploads/2018/07/de4dot.png?resize=677%2C343&ssl=1)](https://i2.wp.com/www.muminkoykiran.com/blog/wp-content/uploads/2018/07/de4dot.png?ssl=1)

**Features of De4dot –**

-   Inline methods. Some obfuscators move small parts of a method to another static method and calls it.
-   Decrypt strings statically or dynamically
-   Decrypt other constants. Some obfuscators can also encrypt other constants, such as all integers, all doubles, etc.
-   Decrypt methods statically or dynamically
-   Remove proxy methods. Many obfuscators replace most/all call instructions with a call to a delegate. This delegate in turn calls the real method.
-   Rename symbols. Even though most symbols can’t be restored, it will rename them to human readable strings. Sometimes, some of the original names can be restored, though.
-   Devirtualize virtualized code
-   Decrypt resources. Many obfuscators have an option to encrypt .NET resources.
-   Decrypt embedded files. Many obfuscators have an option to embed and possibly encrypt/compress other assemblies.
-   Remove tamper detection code
-   Remove anti-debug code
-   Control flow deobfuscation. Many obfuscators modify the IL code so it looks like spaghetti code making it very difficult to understand the code.
-   Restore class fields. Some obfuscators can move fields from one class to some other obfuscator created class.
-   Convert a PE exe to a .NET exe. Some obfuscators wrap a .NET assembly inside a Win32 PE so a .NET decompiler can’t read the file.
-   Removes most/all junk classes added by the obfuscator.
-   Fixes some peverify errors. Many of the obfuscators are buggy and create unverifiable code by mistake.
-   Restore the types of method parameters and fields

### **13. Antinet**

With the help of Antinet, you can easily prevent a managed .NET debugger/profiler from working.

**Github Link –** [https://github.com/0xd4d/antinet](https://github.com/0xd4d/antinet)

Most anti-managed debugger code will call _System.Diagnostics.Debugger.IsAttached_ somewhere in _Main()_ to check whether a managed debugger is present. This code doesn’t do that. Instead, it prevents any managed .NET debugger from working by killing the .NET debugger thread. When this thread is killed, no managed .NET debugger can get any debug messages and will fail to work.

### **14. UPX**

UPX is a free, portable, extendable, high-performance executable packer for several executable formats.

**Website Link –** [https://upx.github.io](https://upx.github.io/)

[![](https://i2.wp.com/www.muminkoykiran.com/blog/wp-content/uploads/2018/07/UPX-ultimate-packer.png?resize=606%2C280&ssl=1)](https://i2.wp.com/www.muminkoykiran.com/blog/wp-content/uploads/2018/07/UPX-ultimate-packer.png?ssl=1)

**Features of UPX –**

-   **Excellent compression ratio:** typically compresses better than WinZip/zip/gzip, use UPX to decrease the size of your distribution!
-   Very fast decompression: ~10 MB/sec on an ancient Pentium 133, ~200 MB/sec on an Athlon XP 2000+.
-   **No memory overhead** for your compressed executables because of in-place decompression.
-   **Safe:** you can list, test and unpack your executables. Also, a checksum of both the compressed and uncompressed file is maintained internally.
-   **Universal:** UPX can pack a number of executable formats.
-   **Portable:** UPX is written in portable endian-neutral C++.
-   **Extendable:** because of the class layout it’s very easy to add new executable formats or new compression algorithms.
-   **Free:** UPX is distributed with full source code under the GNU General Public License v2+, with special exceptions granting the free usage for commercial programs as stated in the UPX License Agreement.

### **15. Radare2**

r2 is a rewrite from scratch of radare in order to provide a set of libraries and tools to work with binary files.

Radare project started as a forensics tool, a scriptable commandline hexadecimal editor able to open disk files, but later support for analyzing binaries, disassembling code, debugging programs, attaching to remote gdb servers and its portable.

**Github Link –** [https://github.com/radare/radare2](https://github.com/radare/radare2)

**Official Website –** [http://www.radare.org/](http://www.radare.org/)

[![](https://i0.wp.com/www.muminkoykiran.com/blog/wp-content/uploads/2018/07/radare2.png?resize=799%2C613&ssl=1)](https://i0.wp.com/www.muminkoykiran.com/blog/wp-content/uploads/2018/07/radare2.png?ssl=1)

**Features of Radare2 –**

-   **Architectures:** 6502, 8051, CRIS, H8/300, LH5801, T8200, arc, arm, avr, bf, blackfin, xap, dalvik, dcpu16, gameboy, i386, i4004, i8080, m68k, malbolge, mips, msil, msp430, nios II, powerpc, rar, sh, snes, sparc, tms320 (c54x c55x c55+), V810, x86-64, zimg, risc-v.
-   **File Formats:** bios, CGC, dex, elf, elf64, filesystem, java, fatmach0, mach0, mach0-64, MZ, PE, PE+, TE, COFF, plan9, dyldcache, Commodore VICE emulator, Game Boy (Advance), Nintendo DS ROMs and Nintendo 3DS FIRMs.
-   **Operating Systems:** Android, GNU/Linux, [Net|Free|Open]BSD, iOS, OSX, QNX, w32, w64, Solaris, Haiku, FirefoxOS
-   **Bindings:** Vala/Genie, Python (2, 3), NodeJS, Lua, Go, Perl, Guile, php5, newlisp, Ruby, Java, OCaml, …

### **16. Plasma**

PLASMA is an interactive disassembler. It can generate a more readable assembly (pseudo code) with colored syntax. You can write scripts with the available Python api. This project is still in big development.

**Github Link –** [https://github.com/plasma-disassembler/plasma](https://github.com/plasma-disassembler/plasma)

[![](https://i2.wp.com/www.muminkoykiran.com/blog/wp-content/uploads/2018/07/plasma-1024x570.png?resize=1024%2C570&ssl=1)](https://i1.wp.com/www.muminkoykiran.com/blog/wp-content/uploads/2018/07/plasma.png?ssl=1)

**It supports :**

-   architectures : x86{64}, ARM, MIPS{64} (partially for ARM and MIPS)
-   formats : ELF, PE, RAW

### **17. Hopper**

Hopper Disassembler, the reverse engineering tool that lets you disassemble, decompile and debug your applications.

**Website Link –** [https://www.hopperapp.com/](https://www.hopperapp.com/)

[![](https://i0.wp.com/www.muminkoykiran.com/blog/wp-content/uploads/2018/07/hopper.jpg?resize=960%2C694&ssl=1)](https://i0.wp.com/www.muminkoykiran.com/blog/wp-content/uploads/2018/07/hopper.jpg?ssl=1)

**Features of Hopper –**

-   **Native –** Hopper is perfectly adapted to the environment. The macOS version makes full use of the Cocoa framework, and the Linux version makes use of Qt 5.
-   **Procedures –** Hopper analyzes function’s prologues to extract procedural information such as basic blocks and local variables.
-   **Extensible –** With the Hopper SDK, you’ll be able to extend Hopper’s features, and even write your own file format and CPU support.
-   **Control Flow Graph –** Once a procedure has been detected, Hopper displays a graphical representation of the control flow graph. You can even export a PDF.

### **18. ScratchABit**

ScratchABit is an interactive incremental disassembler with data/control flow analysis capabilities. ScratchABit is dedicated to the efforts of the OpenSource reverse engineering community (reverse engineering to produce OpenSource drivers/firmware for hardware not properly supported by vendors, for hardware and software interoperability, for security research).

**Github Link –** [https://github.com/pfalcon/ScratchABit](https://github.com/pfalcon/ScratchABit)

[![](https://i1.wp.com/www.muminkoykiran.com/blog/wp-content/uploads/2018/07/scratchabit.png?resize=802%2C483&ssl=1)](https://i1.wp.com/www.muminkoykiran.com/blog/wp-content/uploads/2018/07/scratchabit.png?ssl=1)

ScratchABit supports well-known in the community IDAPython API to write disassembly/extension modules.

To use ScratchABit, you need Python3 installed and VT100 (minimum) or XTerm (recommended) terminal or terminal emulator (any Unix system should be compliant, like Linux/BSD/etc., see FAQ below for more).

> git clone –recursive https://github.com/pfalcon/ScratchABit

Kaynak:  [https://www.yeahhub.com/best-19-tools-used-reverse-engineering-2018-update/](https://www.yeahhub.com/best-19-tools-used-reverse-engineering-2018-update/)