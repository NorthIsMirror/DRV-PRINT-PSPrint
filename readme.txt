QUICK GUIDE TO PSPRINT DIFFS

This package contains the source code updates for PSPRINT.DRV (version 30.903),
relative to the IBM DDK sources for the PSCRIPT driver (version 30.800). 

Required:
  src.diff       - contains diffs for the 'src' directory tree
  mri.diff       - contains diffs for the 'mri' directory tree

Optional (see below for explanations):
  makefile.diff  - contains diffs for make scripts (MAKEFILE)
  pakfile.diff   - contains diffs for PAKFILE.LST
  icons.zip      - contains all updated icons
  new_ppds.zip   - contains all newly added PPD files

These diffs assume that you will be building the driver from new subdirectories
within the DDK tree called 'PSPRINT':
  \ddk\print\src\osdd\pscript\psprint   for the source code
  \ddk\print\mri\en\osdd\pscript        for language-dependent files
You can arrange this by XCOPYing the existing 'post32' directories to these new
names.  

If you prefer to keep your modified driver source in the 'post32' directories
(or even use different names again), you can use the -p option with GNU patch
to modify the target paths accordingly.

The MAKEFILE diffs are provided separately as they will probably not be wanted
if you are patching a different version of the PostScript driver (such as 
ECUPS).  These patches only do three things, none of which would be needed in
such circumstances:
 - Set the name of the driver to PSPRINT.
 - Set the name of the corresponding source (and target build) directories to 
   PSPRINT as well.
 - Change the driver BLDLEVEL version number to a custom value (coded in the
   MAKEFILE itself) - current 30.90x.

Similarly, the diff for PAKFILE.LST is provided separately in case you prefer
not to add the new PPDs to your driver.


APPLYING THE CHANGES

Using GNU patch (it is assumed that you know how) from the '\ddk\print'
directory, apply 'src.diff' and 'mri.diff'.

If (and only if) you will be building the driver named 'PSPRINT' (from the
equivalently-named directories): also apply 'makefile_diffs' and
'pakfile.diff'; and unzip 'new_ppds.zip' into the '\ddk\print\mri\en\osdd\ppd'
directory.

Whatever driver you are building, if you want to use the updated (and much
prettier) icons, unzip the file 'icons.zip' into the 
'\ddk\print\src\osdd\pscript\psprint' directory.


Direct any questions to (almost-usable address): alex at altsan dot org.

-- 
Alex Taylor
January 2015
