PSION ORGANISER II IP SUBNET CALCULATOR
=======================================

This is a program written in OPL for the Psion Organiser II series (LZ and
LZ64) which calculates information about IPv4 subnets given an address and
netmask:

* base (bottom) address
* broadcast (top) address
* netmask / hostmask / mask length given one of these
* the address in hexadecimal
* router addresses for a variety of addressing schemes
* number of addresses in the block

The program is about 6KB in source code and tokenises to about 3KB.

There is also a version for the CM and XP models which has some minor
differences - primarily for the screen size but also to cope with some
language omissions on those models.

Program procedures
------------------

The program consists of six separate procedures:

* `IPSUBNET.OPL` - the main program for LZ and LZ-64 models
* `IPSUBNET-XP.OPL` - the main program for CM and XP models be renamed
  `IPSUBNET.OPL` when transferred to the Psion
* `IPCALC$.OPL(offset%)` - given an network base address in `net%(4)` and mask
  length in `masklen%`, this calculates the IP address `offest%` addresses from
  the start and returns it as a string using `IPSTR$()`
* `IPSTR$.OPL(ip1%,ip2%,ip3%,ip4%)` - returns the string representation of the
  specified IP address
* `IPINPUT.OPL(prompt$,default$)` - prompts the user to enter an IP address
  (or netmask) using the specified prompt and default value; the address is
  parsed and returned into the global array `ip%(4)`
* `IHXSTR$.OPL(ip1%,ip2%,ip3%,ip4%)` - hex version of `IPSTR$.OPL` but returns
  the address in the format of an 8-digit hex string
* `IHXINPUT.OPL(prompt$,default$)` - hex version of `IPINPUT.OPL` but with the
  address in the format of an 8-digit hex string; it also copes with the
  use of the shifted-equivalents of the letter keys A-F ("<>()%/")

Saved data
----------

The information entered is stored in a data file called on `A:IPSUBNET.ODB`
(in the internal RAM) to be restored upon next start up.

If the file is not present, it is created automatically with some defaults.

If the program is removed, this file will need to be manually deleted.
