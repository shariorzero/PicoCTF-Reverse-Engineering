# picoCTF-crackme-py

### Description:
  * Hiding this really important number in an obscure piece of code is brilliant!
  * AND it's encrypted!
  * We want our biggest client to know his information is safe with us.

### Solution:
  Check for all the code. It hides a `bezos_cc_secret`. This is our client information encrypted. Now let's call method `decode_secret` and give bezos_cc_secret as parameter.
  
  
  $ decode_secret(bezos_cc_secret)

# Answer: 
  picoCTF{1|\/|_4_p34|\|ut_ef5b69a3}
