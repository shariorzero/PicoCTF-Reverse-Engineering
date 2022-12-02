# picoCTFARMssembly-1
### Description
  For what argument does this program 
  print `win` with variables 68, 2 and 3? 
  File: chall_1.S 
  Flag format: picoCTF{XXXXXXXX} -> 
  (hex, lowercase, no 0x, and 32 bits. ex. 5614267 would be picoCTF{0055aabb})
  

link: https://play.picoctf.org/practice/challenge/160?category=3&page=1

### Solution:

1. Learn armv8 assembly and understand procedure of chall_1.s
2. Using simulator and run on linux platform.
3. Same as 2 but no need of any simulator. Use IDA pro for understanding the code.   


Here I am using method 2 and 3.
* Method 3 : Method 2(1-4) and then open <b>chall_1</b> in <b>IDA Pro</b>.
    
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
5. Now open <b>chall_1</b> in <b>IDA pro</b>
6. In the main it looks for a function which defines where it shows win! and where it shows lose!
7. The main function shows 
  ```sh
  int __cdecl main(int argc, const char **argv, const char **envp)
  {
    unsigned int v4; // [xsp+2Ch] [xbp+2Ch]

    v4 = atoi(argv[1]);
    if ( (unsigned int)func(v4) )
      return puts("You Lose :(");
    else
      return puts("You win!");
  }
  ```
9. func() is
  ```
  __int64 __fastcall func(int a1)
  {
    return (unsigned int)(90 - a1);
  }
  ```
11. So run
   ```sh
   ./chall_1 90
   ```
   Output: you win!
### Answer:
So answer is 32 bit hexadecimal value of 90.
In hexadecimal: 0000005a


Flag: <b>picoCTF{0000005a}</b>

   
    
