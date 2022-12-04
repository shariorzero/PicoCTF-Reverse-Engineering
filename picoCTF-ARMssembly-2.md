# picoCTFARMssembly-2
### Description
What integer does this program print with argument 2403814618? 
File: chall_2.S 
Flag format: picoCTF{XXXXXXXX} -> (hex, lowercase, no 0x, and 32 bits. 
ex. 5614267 would be picoCTF{0055aabb})
  

link: https://play.picoctf.org/practice/challenge/160?category=3&page=1

### Solution:

1. Learn armv8 assembly and understand procedure of chall_1.s
2. Using simulator and run on linux platform.
3. Same as 2 but no need of any simulator. Use IDA pro for understanding the code.   


Here I am using method 2 and 3.
* Method 2
    
1. Install binutils-aarch64-linux-gnu
   ```sh
   sudo apt install binutils-aarch64-linux-gnu
   ```
3. Compile assmbly
   ```sh
   aarch64-linux-gnu-as -o chall_1.o chall_1.S
   aarch64-linux-gnu-gcc -static -o chall_1 chall_1.o
   ```
4. Install install a version of QEMU emulator to run arm binaries as a normal program
   ```sh
   sudo apt install qemu-user-static
   ```
5. Now run
   ```sh
   ./chall_2 2403814618
   ```
   Output: Result: 2916476558

### Answer:
So answer is 32 bit hexadecimal value of 2916476558.
In hexadecimal: ADD5E68E


Flag: <b>picoCTF{ADD5E68E}</b>

   
    
