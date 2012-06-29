Golden Master files for Trivia
==============================

Trivia is a terrible, terrible piece of software, which is why it's perfect for use in practicing working with legacy code. One of the most important things to do when dealing with old, crufy codebases is to create a regression test suite. This is what these three shell scripts do: create a "Golden Master" which stops you from making stupid mistakes while you get the code properly under test.

Step 1
------
Generate some regression tests. Adapt your entry point so it takes one argument, a random seed, and use that to seed your random number generator. Then run this:

    generate "<your command here>" "<number of tests to create>" "<output directory>"

Running against the Java code, it took one and a half minutes on a fairly beefy computer to generate 1000 test cases. You're better off reimplementing this in your language of choice so you don't have the initialisation overhead, but these scripts will do in a pinch.

Step 2
------
Go change your code.

Step 3
------
Verify your changes.

    verify "<your command here>" "<output directory>"

Step 4
------
You can do one of three things here.

If your code passes, good. Commit.

If your code doesn't pass and you were expecting it to, revert.

If your code doesn't pass because you deliberately made some changes in the output, bless your changes:

    bless "<your command here>" "<output directory>"

Step 5
------
Repeat.
