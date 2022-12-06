# transformation enc
link: https://play.picoctf.org/practice/challenge/104?category=3&page=1

### Description:
I wonder what this really is... enc ''.join([chr((ord(flag[i]) << 8) + ord(flag[i + 1])) for i in range(0, len(flag), 2)])

### solution: 
chech file type in linux terminal. It shows Unicode text, UTF-8 text, with no line terminators.
This kind of file can be cracked using python. Just do same as below described.


    * copy text from enc file.
    * open python in terminal.
    * type 
        decode = '灩捯䍔䙻ㄶ形楴獟楮獴㌴摟潦弸彥ㄴㅡて㝽'
        print(decode.encode('utf-16-be'))
    * output = b'picoCTF{16_bits_inst34d_of_8_e141a0f7}'
    
FLAG = <b>picoCTF{16_bits_inst34d_of_8_e141a0f7}</b>
