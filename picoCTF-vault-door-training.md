# PicoCTF-ARMssembly-0
### Description:
    Your mission is to enter Dr. Evil's laboratory and retrieve 
    the blueprints for his Doomsday Project. The laboratory is protected 
    by a series of locked vault doors. Each door is controlled by a 
    computer and requires a password to open. Unfortunately, our undercover 
    agents have not been able to obtain the secret passwords for the vault 
    doors, but one of our junior agents obtained the source code for each 
    vault's computer! You will need to read the source code for each level 
    to figure out what the password is for that vault door. As a warmup, 
    we have created a replica vault in our training facility. 
    The source code for the training vault is here: VaultDoorTraining.java


### link: https://play.picoctf.org/practice/challenge/7?category=3&page=1

### Solution:
Just open the code. It shows a password check method. That method contains the
password.
    
1. open code on terminal
   ```sh
   cat VaultDoorTraining.java
   ```
3. check and get password
   ```sh
   public boolean checkPassword(String password)
     return password.equals("w4rm1ng_Up_w1tH_jAv4_3808d338b46");
   }
   ```
    
Flag: <b>picoCTF{w4rm1ng_Up_w1tH_jAv4_3808d338b46}</b>

<p align="right">(<a href="#readme-top">back to top</a>)</p>
