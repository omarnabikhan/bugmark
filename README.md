Bugmarker is a tool for programmers keep track of where they are at in all of
their projects. In the midst of debugging you can create a bugmark with some
information on where you think the bug is, what is happening, what commands you
are running etc and then move onto something else without fear of forgetting
where you were in the debugging process. You may have any number of bugmarks
for a particular project and mark them resolved as you solve them. Bugmarks
are analagous to commits in the popular VCS git, if that helps you understand
them. Bugmarks are best for small bugs you've identified in a single directory
or even a single file; they are not intended for large bugs between different
modules. For those, you're better off with a more heavy duty bug-tracking system
(and probably distributed since you probably aren't coding something of that
scale alone). Now we'll go through a typical workflow with bugmark.

Here is how to create a bugmark:  

`$ bugmark mark <bug name> <bug description>`  
or  
`$ bugmark mark <bug name>`  
which will put you into your editor of choice to write the description of the
bug. You may not have duplicate names. If you think you do, you should probably
resolve your old bugmark. Marking will also create a timestamp on that bug that
you can use later for checking in on stale bugs.  

If your project has a few bugmarks you can get a list of them via  
`$ bugmark list`  
which will list the names of all the bugmarks created in the PWD. This implies
that subdirectories have independent bugmarks (as we mention earlier).  

Once a bugmark is created, you can read the description of that bug via  
`$ bugmark info <bug name>`  
which will print out the description you wrote earlier.  

Once you resolve this bug you can mark it resolved (delete it) it via  
`$ bugmark resolve <bug name>`  
which also makes the name of that bug available (if you run into the same bug
or very similar bug).  

If you make significant progress on a bug but don't quite resolve it you can
update your bug via  
`$ bugmark update <bug name> <update>`  
or  
`$ bugmark update <bug name>`  
which like the `mark `command, will put you in an editor to write the update.
The update is appended to the previous description with a divider that contains
a timestamp.  

Like we said earlier, you can get a list of your stale bugs. The command is:  
`$ bugmark stale`  
which will give you a list of all the stale bugmarks in the PWD. If you want a
list of all your stale bugmarks you may use a flag:  
`$ bugmark stale --all`

By default, stale is defined as living for longer than 7 days, but you can
configure this via:  
`$ bugmark configure stale=X`  
where `X` is the (integer) number of days stale is defined as. Each directory
with bugmarks can have its own definition of stale.  
