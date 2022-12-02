# PicoCTF-ARMssembly-0
### Description:
    What integer does this program print with arguments 4134207980 and 950176538? 
    File: chall.S Flag format: picoCTF{XXXXXXXX} -> (hex, lowercase, no 0x, and 32 bits. 
    ex. 5614267 would be picoCTF{0055aabb})


### link: https://play.picoctf.org/practice/challenge/160?category=3&page=1

### Solution:

There are mainly 3 technique I found. 
1. Learn armv8 assembly and understand procedure of chall.s.
2. Using simulator and run on linux platform.
3. Same as 2 but no need of any simulator. Use IDA pro for understanding the code.   


Here I am using method 2 and 3.
* Method 2 : Need a cross compiler to run arm v8 on non-arm-v8. Then compile it.
* Method 3 : Method 2(1-4) and then open <b>chall</b> in <b>IDA Pro</b>.
    
1. Install binutils-aarch64-linux-gnu
   ```sh
   sudo apt install binutils-aarch64-linux-gnu
   ```
3. Compile assmbly
   ```sh
   aarch64-linux-gnu-as -o chall.o chall.S
   aarch64-linux-gnu-gcc -static -o chall chall.o
   ```
4. Install install a version of QEMU emulator to run arm binaries as a normal program
   ```sh
   sudo apt install qemu-user-static
   ```
5. Run
   ```sh
   ./chall 182476535 3742084308
   ```
### Answer:
    Output in Decimal: 3742084308
    
    
    Convert it in Hexadecimal: df0bacd4
    
    
Flag: <b>picoCTF{df0bacd4}</b>

<p align="right">(<a href="#readme-top">back to top</a>)</p>
