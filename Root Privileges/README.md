# Root Permissions

## What is the difference between `root ALL=(ALL:ALL) ALL` and `root ALL=(ALL) ALL`?

root ALL=(ALL:ALL) ALL  <br>
A     B = ( C : D ) E 

 kush     boulder = (operator) /bin/ls, (root) /bin/kill, /usr/bin/lprm <br>
Then user kush is now allowed to run /bin/ls as **operator**, but /bin/kill and /usr/bin/lprm as **root**.

We can extend this to allow kush to run /bin/ls with either the user or group set to operator:

 kush     boulder = (operator : operator) /bin/ls, (root) /bin/kill, /usr/bin/lprm <br>
We can infer that, given a sudoers line of the form:

D refers to the groups that can be used.





## root ALL=(ALL:ALL) ALL

The first field indicates the username that the rule will apply to
(root).

First “ALL” indicates that this rule applies to all hosts.

Second “ALL” indicates that the root user can run commands as all
users.

Third “ALL” indicates that the root user can run commands as all
groups.

Forth “ALL” indicates these rules apply to all commands.
