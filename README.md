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
S1000 requires special / custom RAM cards: 2MB / 8MB / 32MB  </br>

Disadvantage: Both use similar Screen 240x64 </br>
both screens fail. </br>

Akai Floppy drive is Brand Name </br>
Kurzweil floppy seem OEM </br>
both can be replaced with Gotek + Flash Floppy FW or Gotek + HxC FW </br>

Kurzweil OS had many updates over the years, </br>
problem is that there is 2 versions of the Board  </br>
Early / Late, identified with different letters at Boot time, </br>
or open the machine and see C or J on the Eproms when Screen does Not work. </br>

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

[Mitsubishi](https://en.wikipedia.org/wiki/Mitsubishi_740): M37450M8 CPU are based on [WDC 65C02](https://en.wikipedia.org/wiki/WDC_65C02) based on--> [MOS 6502](https://en.wikipedia.org/wiki/MOS_Technology_6502) </br>
65C02 "CMOS" has +12 New instructions +2 New addressing modes "70 total" vs. MOS 6502 "NMOS" 56-total, both RISC type.</br>
M37450 has small Page 0 at the end of memory space "cache" </br>
first 256 bytes of memory are [reserved](https://en.wikipedia.org/wiki/Zero_page) </br>

Akai S1000 NEC V50 CPU is based on intel [80186](https://en.wikipedia.org/wiki/Intel_80186) + custom instructions + [8088](https://en.wikipedia.org/wiki/Intel_8088) emulation mode that requires special Assembler instuction to Activate. </br>
8086/8088 "x86" has 133 instructions, Z80 has 155, both CISC type. </br>

Examples to compare performance between: NEC V20 vs. V30 vs. intel </br>
[Wolf3D 8088 on V30](https://www.youtube.com/watch?v=UwfzMId3XPs&t=34s) does Not work on Nec v30 without activating special assembler instruction. </br>
[Doom 8088](https://github.com/FrenkelS/Doom8088) or [RealDOOM](https://github.com/sqpat/RealDOOM) 16-Bit version </br>
Wolf3D [CGA on 8086](https://www.youtube.com/watch?v=1t8veCWqQQo).[git](https://github.com/jhhoward/WolfensteinCGA) </br>
[Doom 8088 on 386sx 20MHz](https://www.youtube.com/watch?v=L-jWabyuUkM&t=4s) </br>
[Book 8088 V20](https://www.youtube.com/watch?v=6bODiZ5bP84&t=222s) -> [Updated](https://www.youtube.com/watch?v=CPT6nzopPDw&t=210s) -> [Wold3D CGA on KM18](https://www.youtube.com/watch?v=CPT6nzopPDw&t=938s)</br>
[Wold3D CGA on IBM 5150](https://www.youtube.com/watch?v=auVLqRJCOJ4&t=13s) </br>
[NEC v20 review](https://www.youtube.com/watch?v=Z1u-IrBT9hE&t=17s) </br>
[Wolf3D on IBM Model30 with V30 upgrade](https://www.youtube.com/watch?v=MeJTtX7vSag&t=199s) </br>
[286 vs. V30](https://www.youtube.com/watch?v=CTc9Orx89Mk&t=25s) </br>
Doom & Wolf3D on Amiga1200 [Motorola 68030/68060](https://www.youtube.com/watch?v=wsADJa-23Sg&t=767s) </br>
Doom on C64 + RAD Expansion ["Pi3 CPU"](https://www.youtube.com/watch?v=zAla_RtPECE&t=1767s) </br>

[6502 vs. M6809 vs. Z80](https://www.youtube.com/watch?v=p5mwMwwM-R0&t=3s) </br>
count 10k loops in MS Basic & measure time with a Stopwatch: </br>
6502 | 1.8432MHz | Ram: 32k </br>
M6809 | 1.8432MHz | Ram: 32k </br>
Z80 | 7.3728MHz | Ram: 56k </br>

    10 FOR I =1 TO 10000 
    20 PRINT I 
    30 NEXT I
    RUN
6502: 38sec x MHz = 70.04 <- at 7.3728MHz should have been: 5.15sec. </br>
        /Mhz = 20.61 </br>
6809: 52sec x MHz = 95.84 <- same clk should have been the same vs. 6502: 38sec. </br>
        /Mhz = 28.21 </br>
Z80: 27sec x MHz = 199.06 <- has clk*4 should have been 9.5sec or 38s/4clk </br>
     27 x 4clk /Mhz = 58.59 </br>
Clock per Clock 6502 seem Faster [here is why](https://www.youtube.com/watch?v=ppEpEugeO3k) </br>
modern CPU's need to count to [>1 Billion](https://www.youtube.com/watch?v=VioxsWYzoJk) in c++ </br>

---------------------------------------

since both Samplers are "very similar" exept Ram </br>
would be interesting to translate Kurzweil J OS based on WDC 65C02 to Intel 80186 / NEC V50 CPU </br>
and Akai S1000 OS/Firmware based on [80186](https://en.wikipedia.org/wiki/Intel_80186)/188/V50 to WDC 65C02 CPU instruction set. </br>

Screen & Floppy code should be very similar, Kurzweil has Akai S1000 floppy compatibility mode </br>
front panel controls: push buttons & rotary wheel are "very similar" </br>

The "Magic" of the Akai S1000 sampler, was the Lo-Fi Time Strech Audio Algorithm used in many EDM genres Jungle, DnB, Trance, House, to stretch vocal samples. </br>
there is even an Akai S1000 Akaizer software emulator for PC/Desktop, but... is Not 100% the same </br>
the magic of S1000 was the Slow CPU with No Branch Prediction, No speculative executions, Low interrupts, No special x86 subnormal instructions, No [8087 co-processor](https://www.youtube.com/watch?v=FaQa9INqZf8) floating point instructions </br>
vs. modern CPU's with millions per second. </br>
Akai S5000/S6000 has a [i386EX 33MHz](https://www.youtube.com/watch?v=BDU1t6HMHR8&t=1846s) there is No Service Manual, No schematics, </br>
Akai S3000XL has [NEC D70236AGD-16 "V53A"](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjemnKDnBDxT6AjNaYp-hCKJqaT9aOm7GmadFiXyUW3y05UPGqp_Xd7kaGe3f2cw507NfSDjNabNbxPgaANLoDXrRpEuHiduPsuIEChfG2XhYVwukkJ0T2WyKmwsFHvh8srOdTWLnDO-unl/s1600/009.JPG) source code compatible with [V20](https://en.wikipedia.org/wiki/NEC_V20) & V30 </br>
V30 is [V20](https://en.wikipedia.org/wiki/NEC_V20) with 16-bit External data bus like [80186](https://en.wikipedia.org/wiki/Intel_80186) but pin compatible with [intel 8086](https://en.wikipedia.org/wiki/Intel_8086) </br>
[V20](https://en.wikipedia.org/wiki/NEC_V20) has 2x 16-bit wide Internal databuses "2x 8088" but 8-bit External data bus multiplexed, similar to [80188](https://en.wikipedia.org/wiki/Intel_80186#80188_series) </br>
V50 is embedded version of V30 </br>
V53 is V33 with 4-channel DMA (μPD71071 / i8237), UART (μPD71051 / i8251), 3x timer/counters (μPD71054 / i8254) & interrupt controller (μPD71059 / i8259). </br>
V33 is V30 with separate address & data buses, instruction Decode done by hardwired logic Not microprogrammed control store, </br>
Throughput is 2x V30 at same clock freq. performance equivalent to intel 80286. </br>
Memory address space is 16M bytes, +2 additional instructions: BRKXA & RETXA </br>
support extended addressing mode, 8080 emulation mode Not supported. </br>
[80188](https://en.wikipedia.org/wiki/Intel_80186#80188_series) is an economic version of [80186](https://en.wikipedia.org/wiki/Intel_80186) with 8-bit External data bus, instead of 16-bit ext-data bus. </br>
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

## M37450M8-197FP </br>
Circuit Function & Organization: </br>
16K-Byte Mask-Prog. ROM,  </br>
384-Byte RAM, </br>
8-bit A-D converter, </br>
8-bit D-A converter, </br>
UART, </br>
DBB, </br>
3-timer, </br>
PWM </br>

Structure: C, Si </br>
Supply Voltage: 5V +/-10% = 4.5v-5.5v Recomended: 4.8v-5.20vdc "+/-4%" </br>
Power Dissipation: 30mW </br>
min cycle time: 0.8µS </br>
Max Freq: 10MHz </br>
Package: 64P4B "dip" or 80P6 <- surface mount </br>

M37450.M2 & M4 are smaller, have: </br>
4K/128 & 8K/256 ROM/RAM </br>

https://dbpedia.org/page/Mitsubishi_740 </br>
https://www.edn.com/09-24-98-mitsubishi-melps740-wdc-w65co2s-edns-25th-annual-microprocessor-microcontroller-director/ </br>
[differences](https://www.cpu-world.com/info/6502/65xx_65Cxx_65SCxx_differences.html).[G-translate](https://www-cpu--world-com.translate.goog/info/6502/65xx_65Cxx_65SCxx_differences.html?_x_tr_sl=en&_x_tr_tl=es&_x_tr_hl=es&_x_tr_pto=tc) </br>
https://archive.org/search?query=MELPS </br>

Development tools: </br>
[Mitsubishi's PC4701 emulator](https://www.renesas.com/en/software-tool/pc4701u-discontinued-product) </br>
IAR Systems (www.iar.com), [2500ad.com](https://web.archive.org/web/20031213195812/http://www.2500ad.com/), [Avocet Systems](https://web.archive.org/web/20130414105218/http://www.avocetsystems.com/company/other/predemo.htm), ByteCraft, </br>
[Universal Cross Assembler C32D/C32W/XDASM](https://web.archive.org/web/19990209091606/http://ourworld.compuserve.com/homepages/UCA/page9.htm). </br>
https://web.archive.org/web/20220103054902/https://www.cdadapter.com/cross32.htm </br>
https://web.archive.org/web/20031003031508fw_/http://jm-micro.com/umps.htm </br>
https://web.archive.org/web/20010406085401/http://www.datasynceng.com/c32doc.htm </br>
https://web.archive.org/web/20010629203512/http://www.datasynceng.com/xdasmdoc.htm </br>

[WDCTools](https://wdc65xx.com/WDCTools) Software-Development-System (SDS) </br>
W65C02S core in the W65C134S microc & W65C816S core in W65C265S have embedded monitors that aid in debugging with SDS. </br>
monitor ROMs have libraries for onboard I/O, timers, UART, & power management. </br>

Other 3rd-party vendors supply hardware-development tools. </br>
[www.wdesignc.com/develop.html](https://web.archive.org/web/20041210183717/http://www.wdesignc.com/develop.html) </br>

[westerndesigncenter.com wdc w65c02s](https://www.westerndesigncenter.com/wdc/w65c02s-chip.php).[g-translate](https://www-westerndesigncenter-com.translate.goog/wdc/w65c02s-chip.php?_x_tr_sl=en&_x_tr_tl=es&_x_tr_hl=es&_x_tr_pto=tc) </br>
https://web.archive.org/web/20070920203620/http://www.renesas.com/fmwk.jsp?cnt=/download_search_results.jsp&fp=/support/downloads/download_results&layerId=1032 </br>
https://web.archive.org/web/20060602014250/http://download.renesas.com/eng/mpumcu/upgrades/in_circuit_emulators/m16c/index.html </br>

[HP Emulator HW](https://archive.org/details/bitsavers_hp64700bro7700EmulatorTechnicalDataNov95_265880) </br>
https://www.masswerk.at/6502/disassembler.html </br>
https://github.com/trebonian/visual6502 </br>

https://6502bench.com/ </br>
[Basic Features](https://www.youtube.com/watch?v=dalISyBPQq8) </br>
[Space Eggs](https://www.youtube.com/watch?v=lSvEr5nCHbY) </br>
[SourceGen Disassembly Demo Projects](https://6502disassembly.com/) </br>
[SourceGen convert: machine-language -> assembly](https://github.com/fadden/6502bench/) .NET 4.6.2 & 4.8 W7 </br>

[cc65 complete cross dev package](https://cc65.github.io/getting-started.html) for 65(C)02 </br>
[source](https://github.com/cc65/cc65) </br>
[Win 32&64 Bin](https://sourceforge.net/projects/cc65/files/) </br>
[Deb Bin/Repo](https://software.opensuse.org/download.html?project=home%3Astrik&package=cc65) </br>
[demos](https://sourceforge.net/projects/cc65/files/contrib/) </br>

[OpCodes](http://6502.org/tutorials/65c02opcodes.html) </br>
[W65c02 Docs](https://wdc65xx.com/support/documentation/) </br>
[MOS 6500 pdf](https://archive.org/search?query=MOS-6500+pdf) </br>

[BenEater](https://eater.net/) tutorial video series </br>
https://github.com/redayzarra/6502-Computer-Guide </br>

### 6502 FPGA VHDL
[for Xilinx Foundation M1.5 SW.zip](https://www.sprow.co.uk/dump/free6502/foundation6502.zip) </br>
[Generic VHDL.zip](https://www.sprow.co.uk/dump/free6502/free6502.zip) </br>
[changes doc from 0.7.zip](https://www.sprow.co.uk/dump/free6502/changes6502.zip) </br>
[Original Free-6502 v0.7.zip "No BCD arithmetic to the ALU"](http://www.pldworld.com/_hdl/4/_ip/Free6502/www/Free6502_v07.ZIP) </br>
[other links1](http://www.pldworld.com/_hdl/4/_ip/Free6502/www/index.html).[2](https://www.sprow.co.uk/dump/index.htm#Free6502) </br>

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

https://web.archive.org/web/20150701140238if_/http://www.cdadapter.com:80/download/cross32.pdf </br>
https://web.archive.org/web/20070203144417if_/http://www.datasynceng.com:80/c32demo.zip </br>
https://web.archive.org/web/20070203114308if_/http://www.datasynceng.com:80/c32dem95.zip </br>
https://web.archive.org/web/20000830093257if_/http://www.datasynceng.com:80/xdemo.zip </br>
https://web.archive.org/web/20000830093303if_/http://www.datasynceng.com:80/dis8051.zip </br>
https://web.archive.org/web/20000830093309if_/http://www.datasynceng.com:80/utility.zip </br>
https://web.archive.org/web/20000830093314if_/http://www.datasynceng.com:80/basic52.zip </br>
https://web.archive.org/web/20160720211638if_/http://www.cdadapter.com/images/c32pix.jpg </br>
https://web.archive.org/web/20190319051104if_/http://www.cdadapter.com/images/c32pix1.jpg </br>
https://web.archive.org/web/20161202021646if_/http://www.cdadapter.com/images/c32w9x.jpg </br>

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

AVR / ARM </br>
https://www.rowley.co.uk/avr/index.htm </br>
https://www.rowley.co.uk/crossworks/open_source_code.htm#CrossWorks%20for%20AVR%20-%20LibUSB-WIN32%20Source%20Code </br>
