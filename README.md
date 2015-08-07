fbp2pm
======
fbp2pm converts wxFormBuilders [1] save files to a perl module using FBP::Perl [2]. xrc2pm distinguishes between dialogs and frames and runs on the command line.

Usage:
------
```
fbp2pm.pl dialog|frame [name] [filename]
```

* [name] is the name of the dialog/frame as set in the wxFormBuilder object properties,
* [filename] is the name of the FBP file and will be the name of the perl module.

Example:
--------
```
fbp2pm.pl frame main main.fbp
```

Opens main.fbp, converts the frame called main and stores the resulting perl code in main.pm.


0. http://sourceforge.net/projects/wxformbuilder/
0. http://search.cpan.org/~adamk/FBP-Perl-0.78/lib/FBP/Perl.pm
