# btcwif (bitcoin wif)
This library allows you to get the WIF (wallet import format) from a private ECDSA key and vice versa.<br>
Algorithms are taken from https://en.bitcoin.it/wiki/Wallet_import_format<br>
The library is meant for Python version 3.6

# Usage
Here's an usage example in the Python shell.<br><br>
Calculate WIF from private key
```
>>> import btcwif
>>> priv = "0C28FCA386C7A227600B2FE50B7CAE11EC86D3BF1FBE471BE89827E19D72AA1D"
>>> wif = btcwif.privToWif(priv)
>>> wif
'5HueCGU8rMjxEXxiPuD5BDku4MkFqeZyd4dZ1jvhTVqvbTLvyTJ'
```
Calculate private key from WIF
```
>>> priv1 = btcwif.wifToPriv(wif)
>>> priv1
'0c28fca386c7a227600b2fe50b7cae11ec86d3bf1fbe471be89827e19d72aa1d'
```
Check if WIF is positive to checksum
```
>>> btcwif.wifChecksum(wif)
True
>>> wif1 = "6HueCGU8rMjxEXxiPuD5BDku4MkFqeZyd4dZ1jvhTVqvbTLvyTJ" # invalid WIF
>>> btcwif.wifChecksum(wif1)
False
```
Trying to calculate private key from invalid WIF
```
>>> btcwif.wifToPriv(wif1)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "E:\Programming\bitcoin\btcwif.py", line 86, in wifToPriv
    if not wifChecksum(wif) : raise Exception('The WIF is not correct (does not pass checksum)')
Exception: The WIF is not correct (does not pass checksum)
```
