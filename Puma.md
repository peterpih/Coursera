###DevKit


##JSON Gem

###Puma Gem
This worked, from: https://groups.google.com/forum/#!topic/rubyinstaller/RkBqA6DsGl0  
```
This is how I did it. 

**ruby 2.2.1 x86 32bit version** from rubyinstaler.org site  
**Devkit 4.7.2 32bit** from rubyinstaller.org site this one:  
http://dl.bintray.com/oneclick/rubyinstaller/DevKit-mingw64-32-4.7.2-20130224-1151-sfx.exe?direct 
**openssl** from http://packages.openknapsack.org/openssl/openssl-1.0.0k-x86-windows.tar.lzma   

Ruby unpacked to C:\ruby,  DevKit unpacked to C:\devkit, C:\ruby\bin 
added to path. 
Unpack openssl-1.0.0k-x86-windows.tar.lzma to C:\openssl 

Open console (run cmd.exe) 
Run: C:\devkit\devkitvars.bat 
Run: gem install puma -- --with-opt-dir=c:\openssl 

If ruby 2.2.1 doesn't work, try with ruby 2.1.5 32bit. 
```
For the openssl, had to use 7-Zip and unpack twice (once for .lzma, once for .tar)
