# [Kurzweil K2000RS (1991-2000)](https://en.wikipedia.org/wiki/Kurzweil_K2000) sampler </br>
###### v1.00000001
-----------

CPU: </br>
    
    Mitsubishi M37450M8 </br>
    Toshiba TMP68301AF-16 </br>
    TC518128AFWL-101LV </br>

    K2MIH 250A </br>
    830106-01 </br>
    74LS145 </br>
    74HC191N </br>
    74HC393 </br>
    74HC74P </br>

    Audio 911 YCA </br>
    33,000µF 16v </br>
    4700µF 25v </br>
    LF351N </br>
    TL074CN </br>

ADC: </br>

    74HCT3770 </br>
    CS8402-CS </br>
    CS8412-CS </br>
    CS5336-KS </br>

Kurzweil K2000 Sampler (1991-2000) </br>
"similar" to [AKAI S1000](https://github.com/juanpc2018/Akai-S1000-Project)-[(1988-1993)](https://en.wikipedia.org/wiki/Akai_S1000) </br>
"advantage" Kurzweil uses 1 side Ram, like S3000XL, S3000 Non XL still requires custom Ram boards. </br>
instead S1000 requires special / custom RAM cards: 2MB / 8MB / 32MB  </br>

Disadvantage: Both use similar Screen 240x64 </br>
both screens fail. </br>

Akai Floppy drive is Brand Name </br>
Kurzweil floppy seem OEM </br>
both can be replaced with Gotek + Flash Floppy FW or Gotek + HxC FW </br>

Kurzweil OS had many updates over the years, </br>
problem is that there is 2 versions of the Board  </br>
Early / Late, identified with different letters at Boot time, </br>
or opening machine and see J on the Eproms when Screen does Not work. </br>

some K2000R did Not come with Analog Input ADC board,  </br>
Schematics available online do Not include ADC board. </br>

### ToDo list: </br>
Reverse Eng. ADC board on KiCAD, Target3001!, Eagle, Sprint-Layout, gEDA, LibrePCB, etc... </br>

------

Firmware/OS update requires Eprom programmer like TL866ii or better, same as Akai S1000. </br>

HW Architecture is "similar" but the interesting part is the CPU differences </br>
Kurzweil has Mitsubishi M37450M8 & Toshiba TMP68301AF-16 </br>
vs. </br>
Akai S1000 NEC V50 CPU. </br>

[Mitsubishi 740](https://en.wikipedia.org/wiki/Mitsubishi_740): M37450M8 CPU are based on [WDC 65C02](https://en.wikipedia.org/wiki/WDC_65C02) based on--> [MOS 6502](https://en.wikipedia.org/wiki/MOS_Technology_6502) </br>
small Page 0 differences at the end of memory space "cache". </br>
first bytes of memory are reserved. </br>
instead: </br>
Akai S1000 NEC V50 CPU is based on Intel [80188](https://en.wikipedia.org/wiki/Intel_80186#80188_series) 186 variant + custom instructions + 8086 emulation mode that requires special Assembler instuction to Activate. </br>
Example: </br>
[Doom 8088](https://github.com/FrenkelS/Doom8088) or [RealDOOM](https://github.com/sqpat/RealDOOM) 16-Bit version does Not work on Nec v50/v30 without activating special assembler instruction. </br>

since both machines are "very similar" exept Ram </br>
would be interesting to translate Kurzweil J OS based on WDC 65C02 to Intel 80186 / NEC V50 CPU </br>
and Akai S1000 OS/Firmware based on [80188](https://en.wikipedia.org/wiki/Intel_80186#80188_series)/186/V50 to WDC 65C02 CPU instruction set. </br>

Screen & Floppy code should be very similar, Kurzweil has Akai S1000 floppy compatibility mode </br>
front panel controls: push buttons & rotary wheel are "very similar" </br>

The "Magic" of the Akai S1000 sampler, was the Lo-Fi Time Strech Audio Algorithm used in many EDM genres Jungle, DnB, Trance, House, to stretch vocal samples. </br>
there is even an Akai S1000 Akaizer software emulator for PC/Desktop, but... is Not 100% the same </br>
the magic of S1000 was the Slow CPU with No Branch Prediction, No speculative executions, "No interrupts", No special x86 subnormal floating point instructions vs. modern CPU's with millions per second. </br>
Akai S5000/S6000 has a [i386EX 33MHz](https://www.youtube.com/watch?v=BDU1t6HMHR8&t=1846s) there is No Service Manual, No schematics. </br>
Akai S3000XL has [NEC D70236AGD-16 "V53A"](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjemnKDnBDxT6AjNaYp-hCKJqaT9aOm7GmadFiXyUW3y05UPGqp_Xd7kaGe3f2cw507NfSDjNabNbxPgaANLoDXrRpEuHiduPsuIEChfG2XhYVwukkJ0T2WyKmwsFHvh8srOdTWLnDO-unl/s1600/009.JPG) source code compatible with [V20](https://en.wikipedia.org/wiki/NEC_V20) & V30 </br>
V30 is [V20](https://en.wikipedia.org/wiki/NEC_V20) with a 16-bit external data bus, V30 is pin compatible with the Intel 8086. </br>
V50 is embedded version of the V30 </br>
V53 is V33 core with 4-channel DMA (μPD71071/i8237), UART (μPD71051/i8251), 3x timer/counters (μPD71054/i8254) & interrupt controller (μPD71059/i8259). </br>
V33 is V30 with separate address & data buses, instruction Decode done by hardwired logic Not microprogrammed control store, </br>
Throughput is 2x V30 at same clock frequency, performance equivalent to Intel 80286. </br>
Memory address space is 16M bytes, +2 additional instructions: BRKXA & RETXA </br>
support extended addressing mode, 8080 emulation mode Not supported. </br>
[80188](https://en.wikipedia.org/wiki/Intel_80186#80188_series) is a economic variant of 80186 with 8-bit external data bus, instead of 16-bit data bus. </br>
includes: clock generator, interrupt controller, timers, wait state generator, DMA channels, & external chip select lines, 16-bit registers & 1 megabyte address range. </br>

#### Problem is: </br>
Kurzweil OS/FW was probably designed in C, and compiled using Byte Craft C38 C compiler + custom LCD library </br>
but Byte Craft company is gone since Owner died in 2019, those CPU's had limited support, unlike Intel 8051 MCU wide support </br>
there is only C38 Compiler Demo Available + Generic LCD library. </br>
there are many websites that claim to sell complete C38 compiler, Unknown / Unverified, seem old/abandoned websites. </br>

would require Asembly manual code translation, line-by-line where possible </br>
Eproms are Not Big = possible, do able. </br>
would require a lot of debug using Digilent Digital Discovery or similar, to make software 100% compatible with different HW architectures. </br>

similar to [JJOS](https://www7a.biglobe.ne.jp/~mpc1000/chart_n.htm) for modern [Akai MPC samplers](https://www.mpc-tutor.com/jjos-tutorials/) </br>
but for older samplers. </br>

### [Byte Craft Compilers](https://www.phaedsys.com/principals/bytecraft/index.html)

    Byte Craft has been producing a select range of highly optimised compilers and development tools since 1976. 
    The current processor targets are shown below. Byte Craft is, like Phaedrus Systems heavily involved in the 
    international standards panels for C.

    Walter Banks CEO and owner of Bytecraft passed away in December 2019. He has been greatly missed by the industry.

    Bytecraft closed at the start of 2020, and with it any possibility of supplying any more Bytecraft compilers. 
    We can make available any documentation we have however there is no possibility of finding anything else.


    Byte Craft
    Byte Craft IDE and Technical papers

    Byte Craft produces some essential technical papers.  
    a must for all new embedded programmers.
    
[224 page introduction to embedded systems development.pdf](https://www.phaedsys.com/principals/bytecraft/bytecraftdata/bcfirststeps.pdf) </br>
[comparison between using C and assembler.pdf](https://www.phaedsys.com/principals/bytecraft/bytecraftdata/bcCversusAssemblyProof.pdf) </br>
[75 page guide to Fuzzy Logic, how use it in most C developments.pdf](https://www.phaedsys.com/principals/bytecraft/bytecraftdata/bcfuzlogic.pdf) </br>

As far as i know: </br>
Byte Craft were the main designers of [MPLAB XC8](https://www.microchip.com/en-us/tools-resources/develop/mplab-xc-compilers/xc8)-[Award-Winning](https://www.microchip.com/en-us/tools-resources/develop/mplab-xc-compilers) highly optimized compiler for AVR MCU's. </br>

Another Option is to create an "Universal Sampler" that can load different Firmwares without modification, </br>
based on MISTer / terasic DE10-nano FPGA + ADC & DAC + MIDI add-on cards + 240x64 screen + detachable front panel controls "keyboard" like Akai S5000 S6000 Samplers </br>

## MELPS740

https://dbpedia.org/page/Mitsubishi_740 </br>
https://www.edn.com/09-24-98-mitsubishi-melps740-wdc-w65co2s-edns-25th-annual-microprocessor-microcontroller-director/ </br>
[differences](https://www.cpu-world.com/info/6502/65xx_65Cxx_65SCxx_differences.html).[G-translate](https://www-cpu--world-com.translate.goog/info/6502/65xx_65Cxx_65SCxx_differences.html?_x_tr_sl=en&_x_tr_tl=es&_x_tr_hl=es&_x_tr_pto=tc) </br>
https://archive.org/search?query=MELPS </br>

Development tools: </br>
[Mitsubishi's PC4701 emulator](https://www.renesas.com/en/software-tool/pc4701u-discontinued-product) </br>
IAR Systems (www.iar.com), 2500AD (www.2500ad.com), and ByteCraft (www.bytecraft.com) offer C compilers. </br>
WDC provides a Software-Development-System (SDS). </br>
W65C02S core in the W65C134S microc & W65C816S core in W65C265S micro have embedded monitors that aid in debugging with SDS. </br>
monitor ROMs have libraries for onboard I/O, timers, UART, & power management. </br>
Avocet (www.avocetsystems.com) and Universal Cross Assembler (http://ourworld.compuserve.com/homepages/UCA/) provide compilers for WDC. </br>
Other third-party vendors supply hardware-development tools. </br>
www.wdesignc.com/develop.html </br>

[westerndesigncenter.com wdc w65c02s](https://www.westerndesigncenter.com/wdc/w65c02s-chip.php).[g-translate](https://www-westerndesigncenter-com.translate.goog/wdc/w65c02s-chip.php?_x_tr_sl=en&_x_tr_tl=es&_x_tr_hl=es&_x_tr_pto=tc) </br>
https://web.archive.org/web/20070920203620/http://www.renesas.com/fmwk.jsp?cnt=/download_search_results.jsp&fp=/support/downloads/download_results&layerId=1032 </br>
https://web.archive.org/web/20060602014250/http://download.renesas.com/eng/mpumcu/upgrades/in_circuit_emulators/m16c/index.html </br>

[HP Emulator HW](https://archive.org/details/bitsavers_hp64700bro7700EmulatorTechnicalDataNov95_265880) </br>

--------------------------

[C38 C Compiler for Mitsubishi MELPS](https://web.archive.org/web/20090412185232/http://www.bytecraft.com/C38_C_Compiler_for_Mitsubishi_MELPS) </br>
C38 C38 | MELPS </br>

Byte Craft Limited C38 Code Development System supports the entire Mitsubishi MELPS740 (38000) series of microcontrollers, which includes: 7600 series, M509xx, M371xx, M374xx & M38xxx. </br>

C38 Code Development System includes: </br>

    an optimizing C Cross-compiler.

    the BCLink linker.

    an Integrated Development Environment and editor.

    a built-in macro cross-assembler.

Features In Detail </br>

Other features of the C38 Code Development System include: </br>

    Highly optimized generated code. Full versions generate ROMable code, demonstration versions generate listing files with assembly.

    part-specific header files describe the unique features of each target device.

    compiler configuration using #pragma directives.

    ports are declared and protected using the #pragma port series of directives

    the #pragma vector directive specifies the location and assigned name for interrupt sources.

    BClink Linker links object files and libraries compiled with c38.exe

    object libraries can be included directly in C source files using Absolute Code Mode.

    named address spaces support the grouping of variables at specific memory locations.

    SPECIAL address space declares variables at special locations such as external devices or internal EPROM.

    LOCAL address space allows you to use local variables.

    extensions to the C language designed specifically for the embedded systems developer. Some extensions include bit-sized data types, binary constants, extended case statements, direct variable placement with the @ symbol, and support for processor-specific functions.

    interrupt handler support in C; makes context saving and restoring easy.

    data types include:

    bit, bits

    char, short, int, long

    register-oriented types for direct access to processor registers when necessary

    selectable 8 or 16 bit int data type.

    packed bit fields in structs.

    include single and multiple lines of inline assembly within a C program with the #asm and #endasm directives

    extensive control over computer-generated initialization.

    generates source-level information required for emulators.

    supports the instruction extensions MUL, 7600

    supports processor specific instructions BRK, CLC, CLD, CLI, CLT, CLV, NOP, PHA, PLA, PLP, ROL, ROR, RRF, SEC, SED, SEI, SET, STP, SEI, WIT

    allows direct access to AC, X, Y, CC registers


---------------------------------------

[C38 - Special Page Access](https://web.archive.org/web/20190314042718/http://bytecraft.com/C38_-_Special_Page_Access) </br>
C38 C38 </br>

MELPS740 family of microcontrollers is based on the 6502 instruction set, </br>
Basic instruction set has been extended & enhanced. </br>
One interesting enhancement is the ability to reserve the last page of memory as a special page to hold commonly used subroutines or subroutines that require quick access "cache" </br>

C38 compiler supports this hardware feature with special modifier: SP_PAGE </br>
This modifier tells the compiler to locate a subroutine in the last page of memory & routines that call these functions will use short calling sequences for the function call. </br>

    char c1,c2,c3; 

    void SP_PAGE test(void); 

    void main(void) 
    { 
     c1=4; 
     c2=2; 
     test(); 
     if ((c1=c1-c2)>=3) NOP();
     if ((c1-c2)>=0) NOP();
    }

    void SP_PAGE test1(void)
    {
     NOP();
     NOP();
    }

    void SP_PAGE test(void)
    {
     NOP();
     NOP();
    }

------------------------------------

### DEMOS zip

https://web.archive.org/web/*/http://bytecraft.com/* </br>

https://web.archive.org/web/19970215010753/http://www.bytecraft.com:80/c38demo.zip </br>
https://web.archive.org/web/19980709211241/http://bytecraft.com:80/lcdlib.zip </br>

https://web.archive.org/web/20020126145810*/http://www.bytecraft.com:80/c6805demo.zip </br>
https://web.archive.org/web/19970215010608/http://www.bytecraft.com:80/c6808dem.zip </br>
https://web.archive.org/web/19980709211119/http://bytecraft.com:80/c6808demo.zip </br>
https://web.archive.org/web/19970215010858/http://www.bytecraft.com:80/cop8demo.zip </br>
https://web.archive.org/web/19980709211052/http://bytecraft.com:80/cop8cdmo.zip </br>
https://web.archive.org/web/20190314144717*/http://www.bytecraft.com:80/COP8C_-_Executing_Initialization_Code </br>
https://web.archive.org/web/19980709211140*/http://www.bytecraft.com:80/mpcdemo.zip </br>
https://web.archive.org/web/19970215010918/http://www.bytecraft.com:80/z8demo.zip
https://web.archive.org/web/19980709211151/http://bytecraft.com:80/z8cdemo.zip
https://web.archive.org/web/20020615152129*/http://bytecraft.com:80/BCLPatch.exe </br>
https://web.archive.org/web/20190315060813/http://bytecraft.com/downloads/Li-ion%20battery%20charger.zip </br>
https://web.archive.org/web/20160409163455/http://www.bytecraft.com/downloads/SAM_software.zip </br>
