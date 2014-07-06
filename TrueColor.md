Here's a test case:
```
printf "\x1b[38;2;255;100;0mTRUECOLOR\x1b[0m\n"
```
* or http://github.com/robertknight/konsole/tree/master/tests/color-spaces.pl
* or https://git.gnome.org/browse/vte/tree/perf/img.sh?h=vte-0-36

According to Wikipedia[1], this is only supported by xterm and konsole.

It's a common confusion about terminal colors... Actually we have this:

plain ascii
ansi escape codes (16 color codes with bold/italic and background)
256 color palette (216 colors+16gray + ansi) (colors are 24bit)
24bit true color (888 colors (aka 16 milion)

The 256 color palete is configured at start, and it's a 666 cube of
colors, each of them defined as a 24bit (888 rgb) color.

This means that current support can only display 256 different colors
in the terminal, while truecolor means that you can display 16 milion
different colors at the same time.

Truecolor escape codes doesnt uses a color palete. It just specifies the
color itself.

[1] https://en.wikipedia.org/wiki/ANSI_color

Here are terminals discussions:
==============================

Now **supporting** truecolor
------------------------

* [st](http://st.suckless.org/) (from suckless) -  http://lists.suckless.org/dev/1307/16688.html
* [konsole](http://kde.org/applications/system/konsole/) - https://bugs.kde.org/show_bug.cgi?id=107487
* [iterm2](http://www.iterm2.com/) - https://code.google.com/p/iterm2/issues/detail?id=218
* all [libvte](http://ftp.gnome.org/pub/GNOME/sources/vte/) based terminals:  https://bugzilla.gnome.org/show_bug.cgi?id=704449
    * **libvte**-based [Gnome Terminal](https://help.gnome.org/users/gnome-terminal/stable/)
    * **libvte**-based [sakura](http://www.pleyades.net/david/projects/sakura) - https://bugs.launchpad.net/sakura/+bug/1202564
    * **libvte**-based [Terminator](http://gnometerminator.blogspot.com/p/introduction.html)
    * **libvte**-based [Lilyterm](http://lilyterm.luna.com.tw/)
    * **libvte**-based [ROXTerm](http://roxterm.sourceforge.net/)
    * **libvte**-based [evilvte](http://www.calno.com/evilvte/)
    * **libvte**-based [Termit](https://github.com/nonstop/termit)
    * **libvte**-based [Tilda](https://github.com/lanoxx/tilda)
    * **libvte**-based [stjerm](https://github.com/stjerm/stjerm)
    * **libvte**-based [tinyterm](https://code.google.com/p/tinyterm)
    * **libvte**-based [GTKTerm2](http://gtkterm.feige.net/)

Parsing ANSI color sequences, but approximating them to 256 palette:
--------------------------------------------------------------------

* xterm
* [mlterm](https://sourceforge.net/projects/mlterm/) - http://sourceforge.net/mailarchive/message.php?msg_id=31828705

**NOT supporting** truecolor:
-----------------------------

* [urxvt](http://software.schmorp.de/pkg/rxvt-unicode.html) -  http://lists.schmorp.de/pipermail/rxvt-unicode/2013q3/001826.html 
* [Terminlogy](https://www.enlightenment.org/p.php?p=about/terminology) (E17) - https://phab.enlightenment.org/T746
* [mrxvt](https://sourceforge.net/projects/materm) - https://sourceforge.net/p/materm/feature-requests/41/
* [aterm](http://www.afterstep.org/aterm.php) - https://sourceforge.net/p/aterm/feature-requests/23/

Here are another console programs discussions:
============================================

* mutt - http://dev.mutt.org/trac/ticket/3674
* mc - http://www.midnight-commander.org/ticket/3145#comment:1
* s-lang library - http://lists.jedsoft.org/lists/slang-users/2014/0000001.html
* ncurses library - https://lists.gnu.org/archive/html/bug-ncurses/2013-10/msg00007.html
* mcabber - https://bitbucket.org/McKael/mcabber-crew/issue/126/support-for-true-color-16-millions-colors
* emacs - http://emacs.1067599.n5.nabble.com/RFC-Add-tty-True-Color-support-td299962.html
* vim - https://bitbucket.org/ZyX_I/vim/commits/branch/24-bit-xterm
* tig - https://github.com/jonas/tig/issues/227