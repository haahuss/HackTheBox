```
┌──(kali㉿kali)-[~/HackTheBox/jarvis]
└─$ ffuf -w /usr/share/seclists/Fuzzing/special-chars.txt -u http://jarvis.htb/room.php?cod=1FUZZ -t 100 

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v2.1.0-dev
________________________________________________

 :: Method           : GET
 :: URL              : http://jarvis.htb/room.php?cod=1FUZZ
 :: Wordlist         : FUZZ: /usr/share/seclists/Fuzzing/special-chars.txt
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 100
 :: Matcher          : Response status: 200-299,301,302,307,401,403,405,500
________________________________________________

$                       [Status: 200, Size: 5916, Words: 308, Lines: 190, Duration: 62ms]
~                       [Status: 200, Size: 5916, Words: 308, Lines: 190, Duration: 62ms]
'                       [Status: 200, Size: 5916, Words: 308, Lines: 190, Duration: 64ms]
@                       [Status: 200, Size: 5916, Words: 308, Lines: 190, Duration: 70ms]
_                       [Status: 200, Size: 5916, Words: 308, Lines: 190, Duration: 71ms]
}                       [Status: 200, Size: 5916, Words: 308, Lines: 190, Duration: 72ms]
>                       [Status: 200, Size: 5916, Words: 308, Lines: 190, Duration: 73ms]
*                       [Status: 200, Size: 5916, Words: 308, Lines: 190, Duration: 75ms]
!                       [Status: 200, Size: 5916, Words: 308, Lines: 190, Duration: 75ms]
/                       [Status: 200, Size: 5916, Words: 308, Lines: 190, Duration: 75ms]
^                       [Status: 200, Size: 5916, Words: 308, Lines: 190, Duration: 64ms]
;                       [Status: 200, Size: 6204, Words: 330, Lines: 191, Duration: 64ms]
"                       [Status: 200, Size: 5916, Words: 308, Lines: 190, Duration: 59ms]
.                       [Status: 200, Size: 6204, Words: 330, Lines: 191, Duration: 61ms]
+                       [Status: 200, Size: 6204, Words: 330, Lines: 191, Duration: 61ms]
?                       [Status: 200, Size: 5916, Words: 308, Lines: 190, Duration: 58ms]
{                       [Status: 200, Size: 5916, Words: 308, Lines: 190, Duration: 58ms]
:                       [Status: 200, Size: 5916, Words: 308, Lines: 190, Duration: 69ms]
<                       [Status: 200, Size: 5916, Words: 308, Lines: 190, Duration: 1029ms]
,                       [Status: 200, Size: 5916, Words: 308, Lines: 190, Duration: 2032ms]
]                       [Status: 200, Size: 5916, Words: 308, Lines: 190, Duration: 2035ms]
-                       [Status: 200, Size: 5916, Words: 308, Lines: 190, Duration: 3043ms]
[                       [Status: 200, Size: 5916, Words: 308, Lines: 190, Duration: 3045ms]
(                       [Status: 200, Size: 5916, Words: 308, Lines: 190, Duration: 3045ms]
)                       [Status: 200, Size: 5916, Words: 308, Lines: 190, Duration: 3046ms]
%                       [Status: 200, Size: 5916, Words: 308, Lines: 190, Duration: 4064ms]
\                       [Status: 200, Size: 5916, Words: 308, Lines: 190, Duration: 4066ms]
`                       [Status: 200, Size: 5916, Words: 308, Lines: 190, Duration: 4066ms]
&                       [Status: 200, Size: 6204, Words: 330, Lines: 191, Duration: 4067ms]
|                       [Status: 200, Size: 5916, Words: 308, Lines: 190, Duration: 4066ms]
#                       [Status: 200, Size: 6204, Words: 330, Lines: 191, Duration: 4066ms]
=                       [Status: 200, Size: 5916, Words: 308, Lines: 190, Duration: 4067ms]
:: Progress: [32/32] :: Job [1/1] :: 7 req/sec :: Duration: [0:00:04] :: Errors: 0 ::
                                                                                                                                                            

```