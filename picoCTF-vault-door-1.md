# PicoCTF-vault-door-training
### Description:
This vault uses some complicated arrays! 
I hope you can make sense of it, special agent.
The source code for this vault is here: VaultDoor1.java


### link: https://play.picoctf.org/practice/challenge/12?category=3&page=1

### Solution:
Just open the code. It shows a password check method. That method contains the
password.
    
1. open code on terminal
   ```sh
   cat VaultDoor1.java
   ```
3. check and get password
   ```sh
   public boolean checkPassword(String password){
     return password.length() == 32 &&
         password.charAt(0)  == 'd' && 
         password.charAt(29) == 'a' &&
         password.charAt(4)  == 'r' &&
         password.charAt(2)  == '5' &&
         password.charAt(23) == 'r' &&
         password.charAt(3)  == 'c' &&
         ......
   }
   ```
4. Rearrange the order from 0 to 31.
    
Flag: <b>picoCTF{d35cr4mbl3_tH3_cH4r4cT3r5_f6daf4}</b>

<p align="right">(<a href="#readme-top">back to top</a>)</p>
