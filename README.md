<div align="center">

## Rebuilding the windows icon cache


</div>

### Description

If you have ever written a program that creates file associations, and has changed the icon associated with these files then this may be of interest. This will tell you how to rebuild the icon cache at runtime, and so display these icons without restarting. I decided to submit this when i tried to find some information on it my self, it took many days of searching to find some very very criptic information on the subject, so i have simplified this and put it up here for you :).
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |2001-11-21 12:57:24
**By**             |[Citizen\_Suicide](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/citizen-suicide.md)
**Level**          |Intermediate
**User Rating**    |5.0 (15 globes from 3 users)
**Compatibility**  |VB 6\.0
**Category**       |[Registry](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/registry__1-36.md)
**World**          |[Visual Basic](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/visual-basic.md)
**Archive File**   |[Rebuilding3644011212001\.zip](https://github.com/Planet-Source-Code/citizen-suicide-rebuilding-the-windows-icon-cache__1-29061/archive/master.zip)





### Source Code

```
In windows 32bit all icons being used by the shell are stored in memory in what is known as the icon cache. Ussually this only gets rebuilt when the program starts up (although windows does a little bit of cleaning up of un-used icons at run-time) and so therefore any change to the windows registry default icons does nothing until windows has restarted.
Using the technique listed here you should be able to produce code that can force windows to rebuild this icon cache, and therefore display any changes at run-time.
I must stress that this technique is not perfect and can produce some strange results, i've noticed that it can make the little shortcut arrow icon appear as a blank box 'behind' the shortcut icon. It's up to you whether you want to use this code or let the user wait to reboot before they see your changes to thier icons.
Anyway...
As it appears there is no single windows api to achieve this, because of this you have to be a little bit clever :)
To do this you must follow these steps:
(1) Get the value held in "HKEY_CURRENT_USER\
Control Panel\Desktop\WindowMetrics Registry key".
You'll want the value held in "Shell Icon Size" (if this throws up an error try "Shell Icon BPP")
(2) Subtract 0ne from this number
(3) Write the number back to the registry
(4) Call SendMessageTimeout HWND_BROADCAST
(5) Reset the key to its original setting
(6) call SendMessageTimeout HWND_BROADCAST once again
Thats it! Theres plenty of articals and source code on this site to change registry entries just do a quick search.
The *.zip has some of the api declares and some code snippets you may find usefull.
```

