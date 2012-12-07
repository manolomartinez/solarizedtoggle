solarizedtoggle
===============

A set of files and a script to toggle [solarized](http://ethanschoonover.com/solarized) dark/light.

The script simply creates symliks, or copies files to the right places whenever one toggles from light to dark or vice versa. I use `urxvt`, `vim`, `zathura` and `mutt`, so that's what it changes; but extending it to other applications is, of course, as trivial as the script itself. 

`Xresources-light` is simply the solarized `Xresources`, modified so as to have the light version of the colour scheme. It remains, thus, under the [license](https://github.com/altercation/solarized/blob/master/LICENSE) that Ethan Schoonover has chosen for solarized. All the other files are public domain.

It works, although some things puzzle me:

* There is no need to change `colors.muttrc` when one toggles. In fact, if you change it, it looks weird.
* If urxvt is set to dark, `background` in `.vimrc` has to be set to `light` and vice versa. 

Now, things you need to do for this to work:

* Delete all colour information from `.Xresources` and add a line such as

    #include "/path/to/Xsolarized"

where `Xsolarized` is the symlink created in lines 11 and 17 of `solarizedtoggle`

* Create a file `solarizedstatus` with the single string "dark" ("light"), and, if you solarize `vim`, a file `solarizedstatusforvim` with the string "light" ("dark")

* If you solarize `vim`, substitute the 

    set background = light/dark

line by

    let &background = readfile('/home/manolo/Scripts/solarizedtoggle/solarizedstatus', '', 1)[0]

That's it, I think. 
