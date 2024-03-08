# PicoCTF-ARMssembly-3
### Description:
What integer does this program print with argument 3634247936? File: chall_3.S Flag format: picoCTF{XXXXXXXX} -> (hex, lowercase, no 0x, and 32 bits. ex. 5614267 would be picoCTF{0055aabb})


### link: https://play.picoctf.org/practice/challenge/106?category=3&page=2&solved=0

### Solution:

There are mainly 3 technique I found. 
1. Learn armv8 assembly and understand procedure of chall.s.
2. Using simulator and run on linux platform.
3. Same as 2 but no need of any simulator. Use IDA pro for understanding the code.   


Here I am using method 3.
* Method 2 : Need a cross compiler to run arm v8 on non-arm-v8. Then compile it.
* Method 3 : Method 2(1-4) and then open <b>chall</b> in <b>IDA Pro</b>.
    
1. Install binutils-aarch64-linux-gnu
   ```sh
   sudo apt install binutils-aarch64-linux-gnu
   ```
3. Compile assmbly
   ```sh
   aarch64-linux-gnu-as -o chall_3.o chall_3.S
   aarch64-linux-gnu-gcc -static -o chall_3 chall_3.o
   ```
4. Open chall_3 in IDA pro(64bit). Take a look at <b>main</b> function. It mainly prints <b>v4</b>. v4 is equal to <b>func1(v3)</b>. Here v3 is our input.
   ```sh
   {
    __int64 v3; // x0
    unsigned int v4; // w0

    v3 = atoi(argv[1]);
    v4 = func1(v3);
    return printf("Result: %ld\n", v4);
  }
  ```
5. <b>func1</b> takes a1 as its parameter. It's the input v3. While loop is accepted until a1>0. The if condition mainly check binary value of a1, if it is 1. If it is
1 then <b>func2(v3)</b> executes. 
  ```sh
  __int64 __fastcall func1(unsigned int a1)
  {
    unsigned int v3; // [xsp+2Ch] [xbp+2Ch]

    v3 = 0;
    while ( a1 )
    {
      if ( (a1 & 1) != 0 )
      v3 = func2(v3);
      a1 >>= 1;
    }
    return v3;
  }
  ```
6. func2 always increases value of v3 by 3. like v3=v3+3.
7. given parameter is 3634247936. It has 13 1's in binary.
8. So answer is 13*3 = 39.


N.B. My simulator didn't work properly. So I try for a c++ code to find 39.
Here is the code:
```sh
#include<iostream>
using namespace std;
int func2(int a1)
{
	return a1+3;
}

int main()
{
  int v3;
  long long int a1 = 3634247936;
  v3 = 0;
  while (a1)
  {
    if ( (a1 & 1) != 0 )
      v3 = func2(v3);
    a1 >>= 1;
  }
  cout<<v3<<endl;
}
```
### Answer:
    Output in Decimal: 39
    
    
    Convert it in Hexadecimal: 00000027
    
    
Flag: <b>picoCTF{00000027}</b>

<p align="right">(<a href="#readme-top">back to top</a>)</p>
