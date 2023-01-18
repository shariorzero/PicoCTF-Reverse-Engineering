# picoCTF-GOGO solution
### Description:
    Hmmm this is a weird file... enter_password. There is a instance of the service running at mercury.picoctf.net:20140.

### link: https://play.picoctf.org/practice/challenge/171?category=3&page=2&solved=0

### Solution:

  Go to terminal and type and run command given below to get into given port.
  ```sh
  nc mercury.picoctf.net 20140
  ```
  It connects and wants a password.
  ```
  Enter Password:
  ```
  Now goto IDA pro/ ghidra and check given file <b>enter_password</b>. It shows a 32 bit key and the key is xor with input and then check for something v4(on IDA) 32 bit.
  ```
   if ( (key[v1] ^ input.str[v1]) == v4[v1] )
  ```
  But v4 is not found. So try dynamic analysis on file. Use GDB for dynamically check. 
  <i>install gdb and also install gef extension of gdb for dynamic analysis</i>
  Now type command 
  ```
  gdb ./enter_password
  ```
  Check IDA for location of code given above.
  ```
  .text:080D4B28                 movzx   esi, byte ptr [esp+eax+36]
  ```
  This should be the location for xor.
  Now create a break point at location 0x080D4B28 and run
  ```
  $ break *0x080D4B28
  $ run
  ```
  Now give a random password and it will give you something like this..
  ```
  gef➤  break *0x080d4b28
Breakpoint 1 at 0x80d4b28: file /opt/hacksports/shared/staging/gogo_1_4641419246175075/problem_files/enter_password.go, line 71.
gef➤  run
Starting program: /home/kali/Downloads/enter_password 
[*] Failed to find objfile or not a valid file format: [Errno 2] No such file or directory: 'system-supplied DSO at 0xf7ffc000'
[New LWP 1853]
[New LWP 1854]
[New LWP 1855]
[New LWP 1856]
Enter Password: aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa

Thread 1 "enter_password" hit Breakpoint 1, 0x080d4b28 in main.checkPassword (input=..., ~r1=0xac) at /opt/hacksports/shared/staging/gogo_1_4641419246175075/problem_files/enter_password.go:71                                                                                                                         
71      /opt/hacksports/shared/staging/gogo_1_4641419246175075/problem_files/enter_password.go: No such file or directory.
[ Legend: Modified register | Code | Heap | Stack | String ]
───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────── registers ────
$eax   : 0x0       
$ebx   : 0x0       
$ecx   : 0x184a0020  →  "aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
$edx   : 0x20      
$esp   : 0x1843ff24  →  0x00000000
$ebp   : 0x59      
$esi   : 0x38      
$edi   : 0x1843ff68  →  0x80d48c2  →  0x2444b60f  →  0x00000000
$eip   : 0x80d4b28  →  <main[checkPassword]+168> movzx esi, BYTE PTR [esp+eax*1+0x24]
$eflags: [zero carry PARITY adjust sign trap INTERRUPT direction overflow resume virtualx86 identification]
$cs: 0x23 $ss: 0x2b $ds: 0x2b $es: 0x2b $fs: 0x00 $gs: 0x63 
───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────── stack ────
0x1843ff24│+0x0000: 0x00000000   ← $esp
0x1843ff28│+0x0004: 0x38313638  →  0x00000000
0x1843ff2c│+0x0008: 0x31663633  →  0x00000000
0x1843ff30│+0x000c: 0x64336533
0x1843ff34│+0x0010: 0x64373236
0x1843ff38│+0x0014: 0x37336166  →  0x00000000
0x1843ff3c│+0x0018: 0x62646235
0x1843ff40│+0x001c: 0x39383338
─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────── code:x86:32 ────
    0x80d4b1f <main[checkPassword]+159> jae    0x80d4b66 <main.checkPassword+230>
    0x80d4b21 <main[checkPassword]+161> movzx  esi, BYTE PTR [esp+eax*1+0x4]
    0x80d4b26 <main[checkPassword]+166> xor    ebp, esi
 →  0x80d4b28 <main[checkPassword]+168> movzx  esi, BYTE PTR [esp+eax*1+0x24]
    0x80d4b2d <main[checkPassword]+173> xchg   ebp, eax
    0x80d4b2e <main[checkPassword]+174> xchg   esi, ebx
    0x80d4b30 <main[checkPassword]+176> cmp    al, bl
    0x80d4b32 <main[checkPassword]+178> xchg   esi, ebx
    0x80d4b34 <main[checkPassword]+180> xchg   ebp, eax
─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────── threads ────
[#0] Id 1, Name: "enter_password", stopped 0x80d4b28 in main.checkPassword (), reason: BREAKPOINT
[#1] Id 2, Name: "enter_password", stopped 0x8091504 in runtime.usleep (), reason: BREAKPOINT
[#2] Id 3, Name: "enter_password", stopped 0x809183f in runtime.futex (), reason: BREAKPOINT
[#3] Id 4, Name: "enter_password", stopped 0x809183f in runtime.futex (), reason: BREAKPOINT
[#4] Id 5, Name: "enter_password", stopped 0x809183f in runtime.futex (), reason: BREAKPOINT
───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────── trace ────
[#0] 0x80d4b28 → main.checkPassword(input=0x184a0020 'a' <repeats 32 times>, ~r1=0xac)
[#1] 0x80d48c2 → main.main()
```
It is now confirmed somewhere at this position (v4 xor key) can be found by checking esp stack. breakpoint location shows esp + 36 and starting point is esp + 4. So go for hexdump and 
run command given below.
```
gef➤  hexdump byte $esp+4
```
Stack shows
```
0x1843ff28     38 36 31 38 33 36 66 31 33 65 33 64 36 32 37 64    861836f13e3d627d
0x1843ff38     66 61 33 37 35 62 64 62 38 33 38 39 32 31 34 65    fa375bdb8389214e
0x1843ff48     4a 53 47 5d 41 45 03 54 5d 02 5a 0a 53 57 45 0d    JSG]AE.T].Z.SWE.
0x1843ff58     05 00 5d 55 54 10 01 0e 41 55 57 4b 45 50 46 01    ..]UT...AUWKEPF.
```
First 32 bits are for = (key xor input) and last 32 bit for = (key xor v4). It is known that if a xor b = c, then b xor c = a. So using this method we can get our v4(this v4 is our desired password)
Now write a script of python for doing such thing.
```
from pwn import *
password = xor(unhex("4a53475d414503545d025a0a5357450d05005d555410010e4155574b45504601"),"861836f13e3d627dfa375bdb8389214e")
print(password)
```
and output is 
<b>b'reverseengineericanbarelyforward'</b>
this is our password. But after password it also want unhashed key. Analyze key for which hash it carries. It's MD5 and after decryption we get our plaintext
<b>goldfish</b> .
```
nc mercury.picoctf.net  20140
Enter Password: reverseengineericanbarelyforward
=========================================
This challenge is interrupted by psociety
What is the unhashed key?
goldfish
Flag is:  picoCTF{p1kap1ka_p1c02720c216}
```

### Answer:

  Flag: picoCTF{p1kap1ka_p1c02720c216}

  <p align="right">(<a href="#readme-top">back to top</a>)</p>
