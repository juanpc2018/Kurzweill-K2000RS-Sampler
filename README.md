# Kurzweill K2000RS Sampler

[Kurzweill K2000RS (1991-2000)](https://en.wikipedia.org/wiki/Kurzweil_K2000) </br>

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

Kurzweil K2000 Sampler 1991 </br>
is "similar" to [AKAI S1000 (1988-1993)](https://en.wikipedia.org/wiki/Akai_S1000) </br>
"advantage" Kurzeweill uses 1 side Ram, like S3000 </br>
instead S1000 requires special / custom RAM cards 2MB / 8MB / 32MB  </br>

Disadvantage: Both use similar Screen 240x64 </br>
both screens fail. </br>

Akai Floppy drive seems higher quality, Kurzeill seem OEM / Generic </br>

Kurzeill OS had many updates over the years, </br>
problem is that there is 2 versions of the Board  </br>
Early / Late, identified with different letters at Boot time, </br>
or opening the machine and see J on the Eproms when Scren does Not work.  </br>

some K2000R did Not come with Analog Input ADC board,  </br>
Schematics available online do Not include ADC board. </br>

Firmware/OS update requires Eprom programmer like TL866ii or better, same as Akai S1000. </br>

HW Architecture is "similar" but the interesting thing is the CPU differences </br>
Kurzeill Mitsubishi M37450M8 & Toshiba TMP68301AF-16 </br>
vs. </br>
Akai S1000 NEC V50 CPU. </br>

M37450M8 CPU's are based on the [WDC 65C02](https://en.wikipedia.org/wiki/WDC_65C02) based on--> [MOS 6502](https://en.wikipedia.org/wiki/MOS_Technology_6502) </br>
some small Page 0 differences. </br>
instead: </br>
Akai S1000 NEC V50 CPU is based on Intel 80186 + custom instructions + 8086 emulation mode, that requires special Assembler instuction to Activate. </br>

since both machines are "very similar", exept Ram </br>
would be interesting to translate Kurzweill J OS based on WDC 65C02 to Intel 80186 / NEC V50 CPU </br>
and translate Akai S1000 OS/Firmware based on 80186/V50 to WDC 65C02 CPU instruction set. </br>

Screen, Floppy code should be very similar, Kurzeil has Akai S1000 floppy compatibility mode </br>
front panel controls "push buittons & rotary wheel are "very similar" </br>

Problem is: </br>
Kurzeil OS was probably desinged in C, and compiled using Byte Craft C38 C compiler + custom LCD library </br>
but Byte Craft company is gone since Owner died in 2019, those CPU's had limited support, unlike Intel 8051 wide support </br>
there is only C38 Compiler Demo Available + Generic LCD library. </br>
there are many websites that claim to sell complete C38 compiler, Unknown / Unverified, seem old/abandoned websites. </br>

would require Asembly manual code translation, line-by-line where possible </br>
Eproms are Not Big = is possible, do able. </br>
would also require a lot of debug to make the software 100% compatible with different HW architectures. </br>


´´´

https://www.phaedsys.com/principals/bytecraft/index.html


### Byte Craft Compilers

Byte Craft has been producing a select range of highly optimised compilers and development tools since 1976. The current processor targets are shown below. Byte Craft is, like Phaedrus Systems heavily involved in the international standards panels for C.

Walter Banks CEO and owner of Bytecraft passed away in December 2019. He has been greatly missed by the industry.

Bytecraft closed at the start of 2020, and with it any possibility of supplying any more Bytecraft compilers. We can make available any documentation we have however there is no possibility of finding anything else.


Byte Craft
Byte Craft IDE and Technical papers

Byte Craft produces some essential technical papers. The 224 page introduction to embedded systems development (click here)
https://www.phaedsys.com/principals/bytecraft/bytecraftdata/bcfirststeps.pdf
is a must for all new embedded programmers.
They also have a paper on the comparison between using C and assembler that is quite surprising.
https://www.phaedsys.com/principals/bytecraft/bytecraftdata/bcCversusAssemblyProof.pdf
Another interesting paper is the 75 page guide to Fuzzy Logic and how you can us it in most C developments. Download it here
https://www.phaedsys.com/principals/bytecraft/bytecraftdata/bcfuzlogic.pdf

´´´

--------------------------

[C38 C Compiler for Mitsubishi MELPS](https://web.archive.org/web/20090412185232/http://www.bytecraft.com/C38_C_Compiler_for_Mitsubishi_MELPS) </br>
C38 C38 | MELPS </br>

The Byte Craft Limited C38 Code Development System supports the entire Mitsubishi MELPS740 (38000) series of microcontrollers, which includes: 7600 series, M509xx, M371xx, M374xx & M38xxx. </br>

The C38 Code Development System includes: </br>

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

The MELPS740 family of microcontrollers is based on the 6502 instruction set, </br>
Basic instruction set has been extended & enhanced. </br>
One interesting enhancement is the ability to reserve the last page of memory as a special page to hold commonly used subroutines or subroutines that require quick access "cache" </br>

The C38 compiler supports this hardware feature with the special modifier SP_PAGE. </br>
This modifier tells the compiler to locate a subroutine in the last page of memory & routines that call these functions will use short calling sequences for the function call. </br>

´´´ 

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

´´´

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
