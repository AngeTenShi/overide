Dans ce challenge on voit qu'on a un login et un serial number

On voit que le login est hashé dans la fonction auth et doit correspondre au serial number

on peut donc récupérer cette fonction dans ghidra et l'executer avec comme input notre login

#include <stdio.h>

int main()
{
    char a1[] = "achansel";
    int v4;
    v4 = (*(a1 + 3) ^ 4919) + 6221293;
    int i;
    for (i = 0; i < 8; ++i )
    {
    	v4 += (v4 ^ *(a1 + i)) % 1337;
    }
    printf("%d\n", v4);
    return(0);
}


avec ce code on obtient le serial à rentrer