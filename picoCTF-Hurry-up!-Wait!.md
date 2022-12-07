# picoCTF-Hurry-up!-Wait!.md

### Description:
  svchost.exe


### link: https://play.picoctf.org/practice/challenge/165?category=3&page=1

### Solution:

  Open https://dogbolt.org/ in browser. Upload svchost.exe . Now open it with IDA pro. 

    
1. Look for decompiler explorer online. Look there is a function called "__int64 __fastcall main(int a1, char **a2, char **a3)" . It shows a function 
  ```sh
  sub_298A();
  ```
3. Go and check it. Then look for functions one after one given at <b>sub_298A()</b>. All of them means a specific character.
  ```sh
  sub_2616();   //p
  sub_24AA();   //i
  sub_2372();   //c
  sub_25E2();   //o
  sub_2852();   //C
  sub_2886();   //T
  sub_28BA();   //F
  sub_2922();   //{
  sub_23A6();   //d
  sub_2136();   //1
  sub_2206();   //5
  sub_230A();   //a
  sub_2206();   //5
  sub_257A();   //m
  sub_28EE();   //_
  sub_240E();   //f
  sub_26E6();   //t
  sub_2782();   //w
  sub_28EE();   //_
  sub_226E();   //7
  sub_2136();   //1
  sub_226E();   //7
  sub_233E();   //b
  sub_23DA();   //e
  sub_230A();   //a
  sub_21D2();   //4
  sub_2956();   //}
  ```

    

Flag: <b>picoCTF{d15a5m_ftw_717bea4}</b>

<p align="right">(<a href="#readme-top">back to top</a>)</p>
