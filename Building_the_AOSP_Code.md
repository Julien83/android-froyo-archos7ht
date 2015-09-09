## Introduction ##

Instructions for Building the AOSP Source.


## Details ##

1.Compiling the AOSP

> a) Open a terminal and go to the top level of build directory:

`cd home/user/android-froyo`

> b) Enter in the following to initiate the compilation process (specifying build parameters):

`. build/envsetup.sh` (creates a build setup file)

`choosecombo` (choose a build configuration)

`make -j4 PRODUCT-generic-user` (Build the source. Choose j2 to reduce cpu usage)
<br>
<br>

2. If you build one flavor and then want to build another, you should run:<br>
<code>make installclean</code> (Guarantees that you don't pick up files installed by the previous flavor.)<br>
<br>

3. Execute <code>m clean</code> to clean up the binaries you just created. You can also execute <code>m clobber</code> to get rid of the binaries of all combos. <i>m clobber</i> is equivalent to removing the //out/ directory where all generated files are stored.<br>
<br>

4. Speeding Up Rebuilds: The binaries of each combo are stored as distinct sub-directories of //out/, making it possible to quickly switch between combos without having to recompile all sources each time. However, performing a clean rebuild is necessary if the build system doesn't catch changes to environment variables or make-files. If this happens often, you should define the <i>USE_CCACHE</i> environment variable as shown below:<br>
<br>
<code>export USE_CCACHE=1</code>
<br>

5. Doing so will force the build system to use the ccache compiler cache tool, which reduces recompiling all sources. ccache binaries are provided in //prebuilt/... and don't need to get installed on your system.<br>
<br>
<br>
<br>
