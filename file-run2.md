# picoCTF-file-run2

### Description:
Another program, but this time, it seems to want some input. What happens if you try to run it on the command line with input "Hello!"?
Download the program here.

Link: https://play.picoctf.org/practice/challenge/267?category=3&page=2

# Solution:
1. given <b>run</b> file is executable in linux platform. So run and give an input 'Hello!' as described in problem description.
2. type on terminal:
  ```sh
  ./run 'Hello!'
  ```
FLAG: <b>picoCTF{F1r57_4rgum3n7_be0714da}</b>
