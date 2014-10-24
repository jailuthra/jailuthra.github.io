---
layout: post
title: "Why we need Revision Control"
tags: [git, linux, open source]
---
{% include JB/setup %}

_This is an adaptation of my
[answer on quora](https://www.quora.com/How-do-I-explain-to-someone-the-difference-between-GitHub-and-Dropbox-Google-Docs-and-Drive/answer/Jai-Luthra)
to a similar question_

While working on a project, if you feel like you want to change the
code a bit, but are not sure that it will work, you'll definitely
want to leave the option to go back to the previous working
code if this new idea fails.

The most ad-hoc way to accomplish that is by commenting out your
working code, do the changes, test them, if it works remove the
commented code; if it doesn't work then figure out another way
or fallback to the previous code.

But commenting out code is not very safe.
What if you discover some bugs in your new changes at a later stage?
(after you've removed the commented-out code). Should we keep all the
code we've ever written in form of comments? Probably not.

Maybe we can do something smarter. Rather than commenting out working
code, we can copy a snapshot of the current state of our source code
directory and back it up somewhere arranged by date or by
version number.

That seems tedious.

Wouldn't it be nice if I just tell a utility to save the current
state and this utility does all the job of copying the snapshot of
the directory, saving it with a SHA hash, compressing it et cetera?
Voila! This is exactly what a
[Revision control system](https://en.wikipedia.org/wiki/Revision_control) is! :)

I can make some changes, and add an explanatory message, and the RCS
(git/svn/...) would save the snapshot (or probably the difference of
this snapshot from the previous one) in a neatly arranged and
compressed folder, and call this new change a `commit`. Various
commits together, mark up checkpoints of changes throughout the
history of the source code. And I can fall back at any point as I
like (that too with just a command to the RCS, rather than digging up
all the backup folders)

This is a very basic and intuitive (atleast to me) introduction to
the need of revision control. Read the Wikipedia articles on
[Git](https://en.wikipedia.org/wiki/Git_%28software%29) and
[Revision control](https://en.wikipedia.org/wiki/Revision_control)
to get more details.