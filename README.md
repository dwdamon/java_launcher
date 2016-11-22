# Java launcher

Helper script to treat Java programs as scripts.

## Daves Comment of changes
I prefer camelCase to train_case so I changed the script from java_launcher to javaLauncher.  Personal preference.

Sometimes I'd like to set environment variables that my java app can use.  So I added a handler for:

   # export: STRING="Hello, World!"

That exports the values into the current environment.

## Overview

Put the `javaLauncher` script in your path and put the following line at the
top of an executable Java source program:

    #!/usr/bin/env javaLauncher

If you use Vim, add the following line:

    # vim:ft=java

Optionally add jars to compile and run with:

    # lib:/home/lk/kiln/teamten/java/dist/teamten.jar

Relative pathnames are relative to your Java script. In addition, all jars
in a `java_lib` directory below the `java_launcher` script will be included.

The source will be compiled, cached, and executed. The source file does not
need a `.java` extension, but it does need to match the name of the class.

## Example

Put this into a file called `helloworld` and make the file executable. The name
of the file must match the name of the class.

    #!/usr/bin/env java_launcher
    # vim:ft=java
    # export:STRING="Hello, world!"

    public class helloworld {
      public static void main(String[] args) {
        System.out.println( System.getenv().get( "STRING" ));
      }
    }

Then run:

    % ./helloworld
    Hello world!

