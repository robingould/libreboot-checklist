# libreboot-checklist
copy and paste this checklist for smooth librebooting !

note about ch341a data line: if you think the data line voltage is going to fry the bios chip, test the following while the controller is connected:
1. current output
2. voltage output 

I think you will quickly realize that any concerns of the controller frying the bios chip are very silly and based in rumor
Annecdotally, it worked for me, and I've looked all over and only ever heard (like 5) people saying "I used to use the ch341a programmer on 50+ thinkpads and LUCKILY never had any problems, and thankfully realized before I fried a computer about the data line being at a dangerous voltage"
Seems silly that these people didn't check the god damn voltage while connected IO lmao 
IF IT AINT BROKE DONT FIX IT @!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
(Worked for me perfectly first try with no issues and I did some ridiculous daisy chaining with both usb extension cables and like 4 dupont cables)

![conversiontherapy](https://user-images.githubusercontent.com/13643473/227591011-5624e770-bea5-4aa1-81e5-db50cedb9fdc.jpg)

**The checklist **

    MAC Address:
    Chip name:
    Flash chip size in MB: 

    [ ] Prep
    [ ] Go to bios on thinkpad, then press F1
    if EC version (Embedded Controller) is different than 1.06 need to update it  https://thonkpeasant.xyz/guides/other/starting.html
    [ ] update EC
    [ ] write down MAC address: 

    [ ] Dissasembly 
    [ ] take apart thinkpad
    https://thonkpeasant.xyz/guides/flashing/t400-libreboot.html
    [ ] for each screw unscrewed, mark the location with tape and a number
        each screw then gets attached with tape to something with the same number
        this can then be used later starting from high numbers and going to low so the order is conserved.

    [ ] separate out motherboard from case/chassis

    [ ] Librebooting
    [ ] clean around connectors with toothbrush and isopropyl alcohol if needed

    [ ] take picture of bios chip and look up specific pin configuration
    [ ] Write down Chip Name:

    [ ] wire up CH341A 

    [ ] connect SOIC clip to chip

    [ ] plug in USB

    [ ] sudo flashrom --programmer ch341a_spi -c {CHIP NAME} -r read1.bin
    [ ] sudo flashrom --programmer ch341a_spi -c {CHIP NAME} -r read2.bin
    [ ] diff read1.bin read2.bin
    AS LONG AS NOTHING SHOWS UP AND THE READS HAVE SOME SIZE YOU'RE GOOD TO GO !! 
    [ ] When doing this you will see how many MB ur flash chip is
    [ ] Flash chip size in MB:

    [ ] Go to this: 
    https://mirrors.mit.edu/libreboot/testing/20221214/roms/
    [ ]CTRL+F "{thinkpad number}\_{CHIP SIZE IN MB}"
    [ ] download the .tar.xz version (be careful :D)
    [ ] open it and cd into it 

    [ ] flashrom --programmer ch341a_spi -w
    (should pop up a bunch of stuff that are .roms starting with ChangeLog and NEWS maybe)
    [ ] look up which rom I want
    [ ] flashrom --programmer ch341a_spi -w seabios_withgrub{thinkpad number}{CHIP SIZE}_libgfxinit_corebootfb_usqwerty.rom
    if this fails, and wants specified chip
    [ ] flashrom --programmer ch341a_spi -c {CHIP NAME, probably second option} -w seabios_withgrub{thinkpad number}{CHIP SIZE}_libgfxinit_corebootfb_usqwerty.rom

    [ ] unplug usb once it says VERIFIED
    [ ] remove clip attaching to bios chip

    [ ] Cooling mod + paint (?)
    https://thonkpeasant.xyz/guides/other/cool.html

    [] quad-core mod
    https://thonkpeasant.xyz/guides/other/quad.html

    [ ] re-assembly, do all steps in reverse, start from highest number screw and work down.
    
    
![beloved](https://user-images.githubusercontent.com/13643473/227591011-5624e770-bea5-4aa1-81e5-db50cedb9fdc.jpg)
   

asdiluhfasdf there she is :D 
