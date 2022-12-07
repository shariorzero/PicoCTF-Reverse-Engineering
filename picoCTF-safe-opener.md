# picoCTF-safe-opener.md
### Description:
  Can you open this safe?
  I forgot the key to my safe but this program is supposed to help me with retrieving the lost key. 
  Can you help me unlock my safe?
  Put the password you recover into the picoCTF flag format like:
  
  
  picoCTF{password}


### link: https://play.picoctf.org/practice/challenge/294?category=3&page=2

### Solution:
Open with any code editor(ex: sublime text).
    
1. There is a method <b>openSafe()</b>
  ```sh
  public static boolean openSafe(String password) {
      String encodedkey = "cGwzYXMzX2wzdF9tM18xbnQwX3RoM19zYWYz";

      if (password.equals(encodedkey)) {
          System.out.println("Sesame open");
          return true;
      }
      else {
          System.out.println("Password is incorrect\n");
          return false;
      }
  }
  ```
3. Found 
  ```sh
  string encodedkey = ""cGwzYXMzX2wzdF9tM18xbnQwX3RoM19zYWYz";
  ```
4. Let's do some cryptography on encodedkey. Open https://gchq.github.io/CyberChef/ and copy paste the encodededkey as input.
  Click on magic tool, which automatically decodes encodedkey using base64 decryption method. 
   ```sh
   pl3as3_l3t_m3_1nt0_th3_saf3
   ```
    
    
Flag: <b>picoCTF{pl3as3_l3t_m3_1nt0_th3_saf3}</b>

<p align="right">(<a href="#readme-top">back to top</a>)</p>
