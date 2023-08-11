# PicoCTF-READY GLAIATOR-0
### Description:
    Can you make a CoreWars warrior that always loses, no ties?
Additional details will be available after launching your challenge instance.


### link: https://play.picoctf.org/practice/challenge/368?category=3&page=2

### Solution:

Steps: 
1. Download the file. And check for the file type.
2. <b>imp.red</b> is our file and now lets search what is .red file. It is mainly a redcode.
3. Let's check what is written inside redcode
   ```sh
   vi imp.red
   mov 0,1
   end
   ```
4. Now main task is to find out how a warrior can loose all time. http://www.koth.org/info/corewars_for_dummies/dummies.html
   websites shows <b>dat</b> will make defeat a warrior.
5. Then edit and write
   ```sh
   dat 0,1
   end
   ```
6. Now start instance and copy and paste nc command to connect netcat.

### OUTPUT:
  ```sh
  Rounds: 100
  Warrior 1 wins: 0
  Warrior 2 wins: 100
  Ties: 0
  You did it!
  picoCTF{h3r0_t0_z3r0_4m1r1gh7_a220a377}
  ```

    
    
Flag: <b>picoCTF{h3r0_t0_z3r0_4m1r1gh7_a220a377}}</b>

<p align="right">(<a href="#readme-top">back to top</a>)</p>
