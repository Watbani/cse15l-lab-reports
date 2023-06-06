# Part 1 – Debugging Scenario

Student's Post

Hello everyone!

I'm working on a project which involves running a Java script from a Bash shell script. Everything seems okay with my Java file but I'm getting a Null Pointer Exception that I can't figure out.

I think the problem might be in my Bash script, but I'm not sure. The exception occurs when the bash script is supposed to pass a filename to the BugProgram.

Here's a screenshot of the error message I'm getting when I run my Bash script:

![Screenshot of Terminal with Null Pointer Exception]

Any help would be appreciated!

TA Response

Hi,

Can you please print out the value of the filename variable that you're passing from the Bash script to your BugProgram just before the Java command?

Please add an echo statement before calling Java command in your bash script like this:

bash

echo $filename
java BugProgram $filename

Then please share the terminal output.

Student's Response

Hello,

I added the echo statement as you suggested and ran the script again. Here's what I got:

![Screenshot of Terminal with Output: Null]

It seems that the filename variable is null when it is being passed to the BugProgram.

Setup Information

The file & directory structure needed:

    /project
        runBugProgram.sh
        BugProgram.java

The contents of each file before fixing the bug:

runBugProgram.sh

bash

#!/bin/bash
filename=$1
java BugProgram $filename

BugProgram.java

java

public class BugProgram {
  public static void main(String[] args) {
    String fileName = args[0];
    System.out.println("Reading file: " + fileName);
    // Code to read file and process data
  }
}

The full command line (or lines) you ran to trigger the bug:

bash

bash runBugProgram.sh

A description of what to edit to fix the bug:

It looks like you are not providing the filename as an argument when running your Bash script. You should run your Bash script with the filename as a parameter, like this:

bash

bash runBugProgram.sh input.txt

Ensure you replace input.txt with your actual file name.

Part 2 – Reflection

One of the most important lessons I learned during the second half of the quarter is how to effectively use debuggers and logging to understand the behavior of my code. I've found that taking the time to trace code execution and understand how data is flowing through my program helps me catch bugs earlier and better understand the systems I'm building. It might take some time to set up, but the insights gained from stepping through code and viewing variable values at runtime are invaluable.
