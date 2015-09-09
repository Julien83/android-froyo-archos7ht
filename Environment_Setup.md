## Introduction ##

This section details the steps required to setup and configure your Linux environment in preparation for building Android.


## Details ##

  1. Install the following packages (most are necessary utilities you will need throughout the course of the build):

> a) Open a terminal and enter the following:

`apt-get install git-core gnupg flex bison gperf libsdl-dev libesd0-dev libwxgtk2.6-dev build-essential zip curl libncurses5-dev zlib1g-dev patch gzip cpio mkcramfs lunch`

> b) Install Sun Java 5 (not available on current Linux distros...must add repos) by adding the necessary repositories to your software sources:

`deb http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted`

`deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted`

`deb http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse`

`deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse`


> c) Install the JDK:

`apt-get install sun-java5-jdk`


> d) Configure the JVM / JDK (Select Java 5 from the list of options for JVM):

`update-alternatives --config java`

<br>

2. Install Valgrind (Find memory leaks, stack corruption, array bounds overflows)<br>
<br>
<code>apt-get install valgrind</code>

<br>

3. Install GCC and G++ 4.3 (Not Latest Version)<br>
<br>
<blockquote>a) Install earlier version by opening terminal and:</blockquote>

<code>sudo apt-get install gcc-4.1 gcc-4.3 g++-4.3</code>


<blockquote>b) Install alternatives by opening terminal and:</blockquote>

<code>sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-4.3 20</code>

<code>sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-4.3 20</code>

<code>sudo update-alternatives --install /usr/bin/cc cc /usr/bin/gcc 30</code>

<code>sudo update-alternatives --set cc /usr/bin/gcc_</code>

<code>sudo update-alternatives --install /usr/bin/c++ c++ /usr/bin/g++ 30</code>

<code>sudo update-alternatives --set c++ /usr/bin/g++</code>


<blockquote>c) Configure alternatives by opening terminal and:</blockquote>

<code>sudo update-alternatives  -- config gcc</code>

<code>sudo update-alternavtives -- config g++</code>
<br>
<br>


4. Install Repo Script (Tool for using Git with Android)<br>
<br>
<blockquote>a) Create a build-specific directory under your home and user folder:</blockquote>

<code>mkdir android-froyo</code>

<blockquote>b) Add the build-specific folder to the PATH:</blockquote>

<code>export PATH=/home/lt/android-froyo:$PATH</code>

<blockquote>c) Verify that the bin folder is now in the PATH listing:</blockquote>

<code>echo $PATH</code>

<blockquote>d) Download the Repo script and make sure it's executable:</blockquote>

<code>curl http://android.git.kernel.org/repo &gt;~/android-froyo/repo</code>

<code>chmod a+x ~/android-froyo/repo</code>

<blockquote>e) Initialize the repo client (<b>DO NOT USE git://android.git.kernel.org/platform/manifest.git</b>)</blockquote>

<code>cd /android-froyo</code>

<code>repo init -u git://github.com/thaplague/android_archos7ht_repo.git</code>

<blockquote>f) Pull down the Android files to your working directory:</blockquote>

<code>repo sync</code>
<br>
<br>

5. Git Tag Input and Verification (must be done as root)<br>
<br>
<blockquote>a) Load the following public key into your GnuPG key database. The key is used to sign annotated tags that represent releases.</blockquote>

<code>sudo gpg --import</code>

<blockquote>b) Paste the key(s) below, and press Control-D to end the input and process the keys.</blockquote>


<pre><code>-----BEGIN PGP PUBLIC KEY BLOCK-----<br>
Version: GnuPG v1.4.2.2 (GNU/Linux)<br>
mQGiBEnnWD4RBACt9/h4v9xnnGDou13y3dvOx6/t43LPPIxeJ8eX9WB+8LLuROSV<br>
lFhpHawsVAcFlmi7f7jdSRF+OvtZL9ShPKdLfwBJMNkU66/TZmPewS4m782ndtw7<br>
8tR1cXb197Ob8kOfQB3A9yk2XZ4ei4ZC3i6wVdqHLRxABdncwu5hOF9KXwCgkxMD<br>
u4PVgChaAJzTYJ1EG+UYBIUEAJmfearb0qRAN7dEoff0FeXsEaUA6U90sEoVks0Z<br>
wNj96SA8BL+a1OoEUUfpMhiHyLuQSftxisJxTh+2QclzDviDyaTrkANjdYY7p2cq<br>
/HMdOY7LJlHaqtXmZxXjjtw5Uc2QG8UY8aziU3IE9nTjSwCXeJnuyvoizl9/I1S5<br>
jU5SA/9WwIps4SC84ielIXiGWEqq6i6/sk4I9q1YemZF2XVVKnmI1F4iCMtNKsR4<br>
MGSa1gA8s4iQbsKNWPgp7M3a51JCVCu6l/8zTpA+uUGapw4tWCp4o0dpIvDPBEa9<br>
b/aF/ygcR8mh5hgUfpF9IpXdknOsbKCvM9lSSfRciETykZc4wrRCVGhlIEFuZHJv<br>
aWQgT3BlbiBTb3VyY2UgUHJvamVjdCA8aW5pdGlhbC1jb250cmlidXRpb25AYW5k<br>
cm9pZC5jb20+iGAEExECACAFAknnWD4CGwMGCwkIBwMCBBUCCAMEFgIDAQIeAQIX<br>
gAAKCRDorT+BmrEOeNr+AJ42Xy6tEW7r3KzrJxnRX8mij9z8tgCdFfQYiHpYngkI<br>
2t09Ed+9Bm4gmEO5Ag0ESedYRBAIAKVW1JcMBWvV/0Bo9WiByJ9WJ5swMN36/vAl<br>
QN4mWRhfzDOk/Rosdb0csAO/l8Kz0gKQPOfObtyYjvI8JMC3rmi+LIvSUT9806Up<br>
hisyEmmHv6U8gUb/xHLIanXGxwhYzjgeuAXVCsv+EvoPIHbY4L/KvP5x+oCJIDbk<br>
C2b1TvVk9PryzmE4BPIQL/NtgR1oLWm/uWR9zRUFtBnE411aMAN3qnAHBBMZzKMX<br>
LWBGWE0znfRrnczI5p49i2YZJAjyX1P2WzmScK49CV82dzLo71MnrF6fj+Udtb5+<br>
OgTg7Cow+8PRaTkJEW5Y2JIZpnRUq0CYxAmHYX79EMKHDSThf/8AAwUIAJPWsB/M<br>
pK+KMs/s3r6nJrnYLTfdZhtmQXimpoDMJg1zxmL8UfNUKiQZ6esoAWtDgpqt7Y7s<br>
KZ8laHRARonte394hidZzM5nb6hQvpPjt2OlPRsyqVxw4c/KsjADtAuKW9/d8phb<br>
N8bTyOJo856qg4oOEzKG9eeF7oaZTYBy33BTL0408sEBxiMior6b8LrZrAhkqDjA<br>
vUXRwm/fFKgpsOysxC6xi553CxBUCH2omNV6Ka1LNMwzSp9ILz8jEGqmUtkBszwo<br>
G1S8fXgE0Lq3cdDM/GJ4QXP/p6LiwNF99faDMTV3+2SAOGvytOX6KjKVzKOSsfJQ<br>
hN0DlsIw8hqJc0WISQQYEQIACQUCSedYRAIbDAAKCRDorT+BmrEOeCUOAJ9qmR0l<br>
EXzeoxcdoafxqf6gZlJZlACgkWF7wi2YLW3Oa+jv2QSTlrx4KLM=<br>
=Wi5D<br>
-----END PGP PUBLIC KEY BLOCK-----<br>
</code></pre>

<blockquote>c) After importing the keys, you can verify any tag with:</blockquote>

<code>git tag -v tagname</code>