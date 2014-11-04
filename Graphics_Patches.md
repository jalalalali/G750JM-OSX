Patching Intel 4600
==========
##1.) Patch libCLVMIGILPlugin for HD4600 OpenCL / OpenGL
> sudo perl -i.bak -pe 's|([\xFF\xFC\x3D])\x86\x80\x12\x04|$1\x86\x80\x16\x04|sg' /System/Library/Frameworks/OpenCL.framework/Libraries/libCLVMIGILPlugin.dylib
>
> sudo codesign -f -s - /System/Library/Frameworks/OpenCL.framework/Libraries/libCLVMIGILPlugin.dylib

The perl command will automatically create a backup under libCLVMIGILPlugin.dylib.bak
Note when patching make sure that you are booting with kext-dev-mode=1 to ensure unsigned kexts will load properly.

Credits: http://www.tonymacx86.com/yosemite-laptop-support/145427-fix-intel-hd4400-hd4600-mobile-yosemite.html

##2.) Patch AppleIntelFramebufferAzul with PikerAlpha's script
> sudo curl -o ~/AppleIntelFramebufferAzul.sh https://raw.githubusercontent.com/Piker-Alpha/AppleIntelFramebufferAzul.sh/master/AppleIntelFramebufferAzul.sh
>
> chmod +x ~/AppleIntelFramebufferAzul.sh
>
> ./AppleIntelFramebufferAzul.sh 0x0a260000 patch /System/Library/Extensions/AppleIntelFramebufferAzul.kext/Contents/MacOS/AppleIntelFramebufferAzul

Credits: http://pikeralpha.wordpress.com/2014/09/16/appleintelframebufferazul-sh-v3-0-beta/