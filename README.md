# OSX Defaults

A place to centralize the great work [@mathiasbynens](http://mths.be/osx) did gathering and foster a community around finding and documenting OS X default configuration from the command-line.

Want to see *all*, and I mean **ALL** of the default values on your system?
Open up your command line and type the following:

```
defaults read > ~/defaults.txt
```

Just want the values for a specific application? No problem. Here's an example: 

```
defaults read -app iTerm
```

Source: [Mac Developer Library](https://developer.apple.com/library/mac/documentation/Darwin/Reference/ManPages/man1/defaults.1.html)