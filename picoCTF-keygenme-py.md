# Keygenme-py(picoCTF)


### Description

Given Python file. You just need to crack the file from trail version to crack version.


### Solution

* open keygenme-trial.py in terminal. 
  $ python keygenme-trial.py
* type c for lisence
* now give a random key.(shouldn't work)
* Now look at the python code.
* 'key_full_template_trial' is our lisence key, where static parts are shown but dynamic parts are hidden using 'xxxxxxxx'. Let's check for dynamic part inside 'check_key' method.
* static parts are all okk. then dynamic parts are checked by sha256 cipher of 'username_trail'.
* Let's print sha256 of username_trial with hexdigest.
  $ print(hashlib.sha256(username_trial).hexdigest
  Output: 09820d032d73c31bd8f4a0532062a239d828a4da0951aeb66da928e843597e35
* Now check for order in check_key method. (0d208392)
* add this in place of dynamic_part.


#### final key: picoCTF{1n_7h3_|<3y_of_0d208392}
