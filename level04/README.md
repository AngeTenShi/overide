Dans cet exercice on voit un code qui se protège contre les shellcode grâce à ptrace et prctl nous allons devoir bypasser ces protections 

Pour ce faire il va falloir trouver un shellcode qui n'appelle pas d'exec