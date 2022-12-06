# picoCTF-GDB-Test-Drive

### Description


  Can you get the flag?
  Download this binary.
  Here's the test drive instructions:
  $ chmod +x gdbme
  $ gdb gdbme
  (gdb) layout asm
  (gdb) break *(main+99)
  (gdb) run
  (gdb) jump *(main+104)


### Solution:
  Follow the instruction.
  1. Download the binary.
  2. Type all test drive instructions one after one as described.
      ```sh
      $ chmod +x gdbme
      $ gdb gdbme
      (gdb) layout asm
      (gdb) break *(main+99)
      (gdb) run
      (gdb) jump *(main+104)
      ```
  4. Get the flag at last command.

FLAG: <b>picoCTF{d3bugg3r_dr1v3_197c378a}</b>
