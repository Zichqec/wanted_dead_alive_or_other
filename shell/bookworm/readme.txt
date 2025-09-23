TERMS:

- feel free to modify the shell
  - DON'T use AI to modify the shell, no matter the use
- you can include this in your distributed ghost, but don't redistribute the shell by itself, please
- do NOT use for commercial work, please!
- do NOT claim as your own work. please keep the credit below in the readme.

bookworm and lectern v1.0.0, by WhatAPhantasia
https://whataphantasia.github.io/projects/ukagaka

------------------------
EXPRESSION GUIDE

\s[0] - default sakura
\s[1] - embarrassed sakura
\s[2] - surprised sakura
\s[3] - worried sakura
\s[4] - sad sakura
\s[5] - smiling sakura
\s[6] - content sakura
\s[7] - angry sakura
\s[8] - nervous smile sakura
\s[9] - embarrassed anger sakura

kero has only one surface: a lectern!

if you want the book dress-up between the sakura and kero to sync (so that the lectern will have the book when the sakura isnt holding it and vice versa,) that's something you need to do ghost-side. here's a function you can put in a YAYA ghost:

//---
OnDressupChanged
{
	//reference0 stores if a dressup was changed on a sakura or a kero.
	//_temp takes this and uses it to determine who to change the dressup from.
	_temp = "\0"
	if !reference0; _temp = "\1"
	
	//if the book has been removed
	if reference1 == "Book" && !reference2; "%(_temp)\![bind,Book,Book,1]"
	//if the book has been given
	elseif reference1 == "Book" && reference2; "%(_temp)\![bind,Book,Book,0]"
}
//---

you can also use OnNotifyDressupInfo in conjunction with a surface checking function, if you're worried about the user changing the dressup outside the menu for some reason. i don't see why you'd need to do this though. 
i'd recommend you look at the page on ukadoc if its something you want to look into: https://ukagakadreamteam.github.io/ukadoc/manual/list_shiori_event.html#OnNotifyDressupInfo

------------------------
COLLISION GUIDE

sakura has two collisions: head, ahoge
have fun, feel free to add any in surfaces.txt :)

------------------------
INTERVAL GUIDE

i recommend using: 
- \s[0] to apply intervals to the neutral mouth for the sakura
- \s[5] to apply intervals to the smile mouth for the sakura

the book in the sakura's hands, on some surfaces, is set up to match the sakura's expression. 
if you'd rather the book stay static, go into surfaces.txt and ctrl+f for //both hands at chest and set the surface you want to be the default one to runonce! (don't forget to set the old one as never!)
if you need any help with this, please don't hesitate to reach out to me on my socials.

available interval list:
---- SAKURA
	80-81: soft blush color
		80: normal blush (default)
		81: deeper blush
	500-599: eyes
        500: normal
		502: lidded
		504: closed
		506: happy closed
	1000-1099: mouths
		1000: neutral closed mouth
		1001: neutral open mouth 1 (ooo)
		1002: neutral open mouth 2 (ohh)
		1003: neutral open mouth 3 (eee)
		1010: smile closed mouth
		1011: smile open mouth 1
		1012: smile open mouth 2
		1020: frown closed mouth
		1021: frown open mouth 1
		1022: frown open mouth 2
	1110-1129: face under-bangs dressups
		1110: glasses
		
	1160-1179: eyebrows
		1160: neutral
		1161: surprised
		1162: nervous
		1163: angry
		
	2000-2999: right arms
		2000: drawn to body/chest
			2001: book surprised
			2002: book nervous
			2003: book angry
		2020: in lap
			2021: book surprised
			2022: book nervous
			2023: book angry
		2040: arms out
			2041: book surprised
			2042: book nervous
			2043: book 
	3000-3999: left arms
		3000: drawn to body/chest
		3020: in lap
		3040: arms out
		3060: hand to cheek/glasses
	
if you want to see more intervals, feel free to look into surfaces.txt :)