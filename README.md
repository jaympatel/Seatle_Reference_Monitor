# Seatle File Size Restriction Reference Monitor


Created a reference monitor (security layer) which stops the user from writing to a file after a specified file size.
Added a function called setmaxfilesize() that will take a file size as parameter and enforce it for the specified file. If a file is longer than the specified size, any data past this point in the file will be truncated. (Since the Repy V2 API does not have a truncate call, implemented this functionality). If a writeat() call is performed at a location at or past the end of the file size limit, a SeekPastEndOfFileError should be raised. If the writeat() starts before the file limit, any data up to the size limit should be written and all other data should be discarded.


Type the following commands at the terminal to run your refernce monitor (security layer) with attack program

python repy.py restrictions.default encasementlib.r2py reference_monitor.r2py test0.r2py



Installation of RestrictedPython(Repy)/Seatle Testbed:

The preferred way to get Repy is installing from source. For this, you check out the required Git repositories, and run a build script. You can always update the repos later, and rebuild, so that you get the latest stable version of the Repy runtime.

Here's how to do that. Assuming you are running on a Unixoid OS,

Create a directory for the required Git repositories
mkdir SeattleTestbed
cd SeattleTestbed

Check out the repos required for building Repy
git clone https://github.com/SeattleTestbed/dist.git
git clone https://github.com/SeattleTestbed/repy_v1.git
git clone https://github.com/SeattleTestbed/repy_v2.git
git clone https://github.com/SeattleTestbed/seattlelib_v2.git

Prepare a build directory, and build into it
cd dist
mkdir ~/path/to/build/dir
python preparetest.py ~/path/to/build/dir
(You will see a few warning messages during building, but they can be ignored for the task at hand.) Once the build script finished, ~/path/to/build/dir contains a ready-to-use copy of the RepyV2 runtime!
