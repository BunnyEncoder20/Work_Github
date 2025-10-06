# Vim Motions

The main playlist I'm following: [Primeagen - Vim As Your Editor](https://www.youtube.com/watch?v=X6AR2RMB5tE&list=PLm323Lc7iSW_wuxqmKx_xxNtJC_hJbQ7R)

## 1. Video 1 - Introductions
Always remember the anatomy of a vim-motion:
```bash
   command count length
```
Commands used:
-  h = left
-  j = down
-  k = up
-  l = right

-  :wq = write, quit
-  w =  one word forward (to the beginning of the word)
-  e = one word forward (to end of the word)
-  b = one word back (to the beginning of the word)
-  can combine numbers with motions to specify how many times that motion is to be done (ex: '3k' -> up 3 lines up)

-  d = delete (dd = delete a line, 'dw' = delete one word forward, 'd7k' = delete 7 line's up - etc.)
-  u = undo last change
-  ctrl + r = redo last change

-  general order of motions: command (ex: d, p) number (3, 5) motion (w, k)
-  i = insert (cursor on left)
-  I = insert at start of the line
-  a = append (cursor on right)
-  A = append at end of line
-  v = enter visual mode
-  Shift + V = enter visual line mode
-  ctrl + v = enter visual x mode)

-  y = "yank" copy
-  yy = "yank" entire line
-  p = "paste" (paste)

## Stage 2 Motions
-  f = find char (after cursor, or left). ';' for next word and "," for previous match
-  F = find char (before cursor, or right). Same controls as previous
-  t = move until just before char (after cursor, or right) uses same controls as find
-  T = move until just before char (before cursor, or left) uses same controls as find
-  <cmd>i<len> = in command. Eg: diw -> deletes in word (regardless of position)
-

## Find Cmds
- :%s/is/isn't/g = in command mode, in entire file (%) search (s) replace all 'is' (/is) with 'isn't' (/isn't) and all occurances of that in the line (/g)
- :s/is/isn't/g = replaces all occurance of the is with isn't in that line (on which the cursor is)
