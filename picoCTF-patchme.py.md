# PicoCTF-patchme.py
### Description:
  Can you get the flag?


  Run this Python program in the same directory as this encrypted flag.


### link: https://play.picoctf.org/practice/challenge/287?category=3&page=2

### Solution:

Download and keep both python file and enc file in same folder. Flag is encrypted in <b>flag.txt.enc</b> file.

    
1. Open python file with any code editor like sublime text or etc.
There are two methods one check for your giver password to encrypt the file and another for decryption of the flag.
I used to change the user password (user_pw) to "1234". 
  ```sh
  def level_1_pw_check():
      user_pw = input("Please enter correct password for flag: ")
      if( user_pw == "1234"):     // Given password was something else. I just changed it to make easier for me.
          print("Welcome back... your flag, user:")
          decryption = str_xor(flag_enc.decode(), "utilitarian")
          print(decryption)
          return
      print("That password is incorrect")
  ```
3. Now run in terminal and give new password.
  ```sh
  python patchme.flag.py
  Please enter correct password for flag: 1234
  ```
4. That's it. Our flag is now decrypted and shown in the terminal.
  ```sh
  Welcome back... your flag, user:
  picoCTF{p47ch1ng_l1f3_h4ck_c4a4688b}
  ```

    
    
Flag: <b>picoCTF{p47ch1ng_l1f3_h4ck_c4a4688b}</b>

<p align="right">(<a href="#readme-top">back to top</a>)</p>
