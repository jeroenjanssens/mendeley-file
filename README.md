mendeley-file
=============

Open files associated with a [Mendeley](http://www.mendeley.com) citation. 


Usage
-----
mendeley-file can be invoked from the command line as follows:

	$ ./mendeley-file key [key ...]

where key denotes the citation key as specified in Mendeley (and also the BibTeX citation key if you export your citations to BibTeX). Please note that the citation key is case-sensitive. Multiple citations keys can be provided. 

If a citation has multiple files associated with it, such as the chapters of a thesis, then all those files are opened.

mendeley-file uses [xdg-open](http://portland.freedesktop.org/xdg-utils-1.0/xdg-open.html) to determine the user's preferred application for opening the file(s).


Integration with VIM
--------------------

Let's say you have the following LaTeX text with two citations.

```latex
The goal of dimension reduction is to map a high-dimensional data set onto a low-dimensional space \citep{roweis2000nonlinear,tenenbaum2000global}. 
```	

By adding the code below to your `.vimrc`, you can open the file by placing the cursor anywhere on the citation key and pressing `<leader>pdf` (my <leader> is `,`).

```vim
fun! MendeleyFile()
   let l:Command = expand("<cword>")
   execute "!~/mendeley-file/mendeley-file " . l:Command
endfun

nmap <silent> <leader>pdf :silent call MendeleyFile()<CR>
```


Dependencies
------------
Python 2.7+


License
-------
BSD
