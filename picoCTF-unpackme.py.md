# picoCTF-unpackme.py
### Description:
  Can you get the flag?
  Reverse engineer this Python program.


### link: https://play.picoctf.org/practice/challenge/314?category=3&page=2
### Solution:
Open using any code editor (ex: sublime text). 

```sh
payload = b'gAAAAABiMD04m0Z6CohVV7ozdwHqtgc2__CuAFGG8rWhZBTL0lhfzp-mhu9LYNMnMQMGO-7tEwy3DJ2Y8yjogvzyojFETwN9YEIPXTnO9F1QnkPypWTgjISGve4gcSerJMs694oKcIdKHuVaSxOg1MMNs5k9iPaBIPU7xOKQqCyhnf_f4yUvLdMcer38BqRptocJNvKlyWN8h7ikoWL0zlssxd8OJyPujMz78HZaefvUouvq6LDtPVqRBJFPgSJYf1nHpHKFa1O0zJ6UpTe6ba3PPAxCVXutNg=='
key_str = 'correctstaplecorrectstaplecorrec'
key_base64 = base64.b64encode(key_str.encode())
f = Fernet(key_base64)
plain = f.decrypt(payload)
exec(plain.decode())
```

It is decoding at plain. So print it and give a random password at terminal.
```sh
print(plain)
```
And now it gives output as shown below.
```sh
python unpackme.flag.py 
What's the password? 123
That password is incorrect.
b"\npw = input('What\\'s the password? ')\n\nif pw == 'batteryhorse':\n  print('picoCTF{175_chr157m45_5274ff21}')\nelse:\n  print('That password is incorrect.')\n\n"
```

Here it print <b>pw = print('picoCTF{175_chr157m45_5274ff21}')</b>

Flag: <b>picoCTF{175_chr157m45_5274ff21}</b>

<p align="right">(<a href="#readme-top">back to top</a>)</p>
