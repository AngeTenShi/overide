on a un printf suivi d'un exit le premier reflex est une format string où on va rediriger le GOT de exit vers notre shellcode


Shellcode : 1\xc0\xb0\xbe\xcd\x801\xc91\xd2Qhn/shh//bi\x89\xe3j\x0bX\xcd\x80

On va faire une stratégie déjà faite avant écrire sur les bits 2 par 2 

le padding est de 10 avec plusieurs test %x %x dans l'input

on va mettre notre shellcode dans l'env et jump dessus


