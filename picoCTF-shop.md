# PicoCTF-ARMssembly-0
### Description:
    Best Stuff - Cheap Stuff, Buy Buy Buy... Store Instance: source. The shop is open for business at 
    <b>nc mercury.picoctf.net 11371</b>.


### link: https://play.picoctf.org/practice/challenge/134?category=3&page=1

### Solution:

1. Download <b>shop</b> and check file type. (That is ELF 32 bit)
2. Decompile using IDA pro.
3. There are too many functions. But take a look at <b>main_get_flag</b> . It
shows that main flag may be somewhere in "flag.txt" file on server.
4. Now look for shop online.
  ```sh
  nc mercury.picoctf.net 11371
  ```
3. It shows
  ```sh
  Welcome to the market!
  ====================
  You have 40 coins
          Item            Price   Count       
  (0) Quiet Quiches       10      12
  (1) Average Apple       15      8
  (2) Fruitful Flag       100     1
  (3) Sell an Item
  (4) Exit
  Choose an option:
  ```
4. Let's go back to the IDA pro and checkout <i>main_menu</i> funciton. <i>Wallet</i> is updated by a code which contains bug!!
   ```sh
   v15 = wallet - *_num * inv.array[v14].price;
   ```
   Suppose wallet is 40 and we want (0) * 4. Then updated wallet = 40 - (4*10) = 0
   So there is a chance that if we give shop a negative number of amount, then our wallet becomes increased like
   wallet = 40-(-6*10) = 40 + 60 = 100
5. Now let's try this
  ```sh
  Choose an option: 
  0
  How many do you want to buy?
  -6
  You have 100 coins
  ```
6. That's it. Buy 2 and it shows flag.
  ```sh
  Choose an option: 
  2
  How many do you want to buy?
  1
  Flag is:  [112 105 99 111 67 84 70 123 98 52 100 95 98 114 111 103 114 97 109 109 101 114 95 98 56 100 55 50 55 49 102 125]
  ```
7. Convert this ascii code into characters using any online ascii converter.


Flag: <b>picoCTF{b4d_brogrammer_b8d7271f}</b>

<p align="right">(<a href="#readme-top">back to top</a>)</p>
