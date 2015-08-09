fbp2pm
======
fbp2pm converts wxFormBuilders [1] save files to a perl module using FBP::Perl [2]. fbp2pm distinguishes between dialogs and frames and runs on the command line.

0. http://sourceforge.net/projects/wxformbuilder/
0. http://search.cpan.org/~adamk/FBP-Perl-0.78/lib/FBP/Perl.pm

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

Bugfix:
-------
When using a Wx::DatePickerCtrl FBP::Perl will die generating the perl code, stating the use of that control is not supported. To fix this, you have to comment out line 1168 of perl5/lib/perl5/FBP/Perl.pm like so:
```
# die "Wx::DatePickerCtrl is not supported by Wx.pm";
```
And as the date picker control does not only depend on Wx::DateTime (which is taken care of by FBP::Perl correctly) but on Wx::Calendar as well, the according use statement has to be added to the perl code after generation:
```
use Wx::Calendar;
```
