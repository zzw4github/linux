General Startup
	To use vi: vi filename
	To exit vi and save changes: ZZ   or  :wq
	To exit vi without saving changes: :q!
	To enter vi command mode: [esc]


Counts
        A number preceding any vi command tells vi to repeat
	that command that many times.




Cursor Movement

	h       move left (backspace)

	j       move down

	k       move up

	l       move right (spacebar)

	[return]   move to the beginning of the next line

	$       last column on the current line

	0       move cursor to the first column on the 
		current line

	^       move cursor to first nonblank column on the
		current line

	w       move to the beginning of the next word or 
		punctuation mark

	W       move past the next space

	b       move to the beginning of the previous word 
		or punctuation mark

	B       move to the beginning of the previous word,
		ignores punctuation

        e       end of next word or punctuation mark

        E       end of next word, ignoring punctuation

        H       move cursor to the top of the screen 

        M       move cursor to the middle of the screen

        L       move cursor to the bottom of the screen 




Screen Movement

       G        move to the last line in the file

       xG       move to line x

       z+       move current line to top of screen

       z        move current line to the middle of screen

       z-       move current line to the bottom of screen

       ^F       move forward one screen

       ^B       move backward one line

       ^D       move forward one half screen

       ^U       move backward one half screen

       ^R       redraw screen 
		( does not work with VT100 type terminals )

       ^L       redraw screen 
		( does not work with Televideo terminals )




Inserting

       r        replace character under cursor with next 
		character typed

       R        keep replacing character until [esc] is hit

       i        insert before cursor

       a        append after cursor

       A        append at end of line

       O        open line above cursor and enter append mode




Deleting

	x       delete character under cursor

	dd      delete line under cursor

        dw      delete word under cursor

        db      delete word before cursor




Copying Code

        yy      (yank)'copies' line which may then be put by
		the p(put) command. Precede with a count for
		multiple lines.




Put Command
        brings back previous deletion or yank of lines,
	words, or characters

        P       bring back before cursor

        p       bring back after cursor



 Find Commands

	?       finds a word going backwards

	/       finds a word going forwards

        f       finds a character on the line under the
		cursor going forward

        F       finds a character on the line under the
		cursor going backwards

        t       find a character on the current line going
		forward and stop one character before it

	T       find a character on the current line going
		backward and stop one character before it

	;	repeat last f, F, t, T




Miscellaneous Commands

	.	repeat last command

	u	undoes last command issued

	U	undoes all commands on one line

	xp	deletes first character and inserts after
		second (swap)

	J	join current line with the next line

	^G	display current line number

	%	if at one parenthesis, will jump to its mate

	mx	mark current line with character x

	'x	find line marked with character x

	NOTE: Marks are internal and not written to the file.




Line Editor Mode
	Any commands form the line editor ex can be issued 
	upon entering line mode.

	To enter: type ':'

	To exit: press[return] or [esc]




ex Commands
	For a complete list consult the 
	UNIX Programmer's Manual




READING FILES
	copies (reads) filename after cursor in file 
	currently editing

	:r filename




WRITE FILE

	:w 	saves the current file without quitting




MOVING

	:#	move to line #

	:$	move to last line of file




SHELL ESCAPE
	executes 'cmd' as a shell command.

	:!'cmd'

