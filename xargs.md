# Xargs
-0 , --null, 用\0结尾
-a file
-d <delim> 只接受单一字符  When processing the input, quotes and backslash are not special; every  character  in  the input is taken literally.    
 The -d option disables any end-of-file string, which is treated like any other argument
 -E eof-str
  -I replace-str
   -L max-lines
    -n max-args
     -P max-procs   the default is 1.  If
              max-procs is 0, xargs will run as many processes as possible  at
              a  time.   Use the -n option or the -L option with -P; otherwise
              chances are that only one exec will be  done.   While  xargs  is
              running,  you  can send its process a SIGUSR1 signal to increase
              the number of commands to run simultaneously, or  a  SIGUSR2  to
              decrease the number.  You cannot increase it above an implemen‐
              tation-defined limit (which is shown with  --show-limits).   You
              cannot  decrease  it  below 1.  xargs never terminates its com‐
              mands; when asked to decrease, it merely waits for more than one
              existing command to terminate before starting another.

 -p, --interactive
 --process-slot-var=name
 --process-slot-var=name--process-slot-var=name--process-slot-var=name
 -r --no-run-if-empty
 -s max-chars The  largest  allowed  value  is
              system-dependent, and is calculated as the argument length limit
              for exec, less the size of your environment, less 2048 bytes  of
              headroom.   If this value is more than 128KiB, 128Kib is used as
              the default value; otherwise, the default value is the  maximum.
              1KiB is 1024 bytes.  xargs automatically adapts to tighter con‐
              straints.

> 
 
--show-limits
              Display the limits on the command-line length which are  imposed
              by the operating system, xargs' choice of buffer size and the -s
              option.  Pipe the input  from  /dev/null  (and  perhaps  specify
              --no-run-if-empty) if you don't want xargs to do anything.

-t, --verbose
       Print the command line on the standard error output before executing it.
-x, --exit
              Exit if the size (see the -s option) is exceeded.
--help Print a summary of the options to xargs and exit.
--version
              Print the version number of xargs and exit.

EXAMPLES
       find /tmp -name core -type f -print | xargs /bin/rm -f

	find /tmp -name core -type f -print0 | xargs -0 /bin/rm -f

	 find /tmp -depth -name core -type f -delete

ritten with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTgzNjEyNzIyOF19
-->