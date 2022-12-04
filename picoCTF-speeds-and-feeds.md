# PicoCTF-speeds-and-feeds
### Description:
There is something on my shop network running at nc mercury.picoctf.net 16524, but I can't tell what it is. Can you?


### link: https://play.picoctf.org/practice/challenge/116?category=3&page=1

### Solution:
Just open the code. It shows a password check method. That method contains the
password.
    
1. type on terminal
   ```sh
   nc mercury.picoctf.net 16524
   ```
   It shows something like code.
3. check for hint
   ```sh
   What language does a CNC machine use?
   ```
4. google for answer and answer is G-code
5. Let's search for G-code simulator. One of them, https://ncviewer.com/
6. Copy code from terminal and paste there and run.
7. It's shows a graphics look-alike picoCTF{num3r1cal_c0ntr0l_1395ffad}

Flag: <b>picoCTF{num3r1cal_c0ntr0l_1395ffad}</b>

<p align="right">(<a href="#readme-top">back to top</a>)</p>
