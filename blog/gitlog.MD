---
title: "Git log"
date: 2018-12-15T07:37:30+03:00
draft: false
---

I always do `git log` and explore what changes were made by other developers.
It is my habit and I don't expect that other developers do the same. But I
would totally be very happy if a git history will become more clean and
understandable not only in big open-source projects but also in a majority
of company in the software development industry. You need to follow some
rules to keep your git history healthy.

## Better Commit Message

* Commit messages are written for the people not just because they must be
  written to be able to merge changes into the main line.
* Commit should have the structure:
    * title:
        * One line.
        * Informative.
        * No more than 80 characters per line.
    * body:
        * Must be separated from the title by one space.
        * More detailed description of the title (if it is really needed).
        * No more than 80 characters per line.
    * reference:
        * Must be separated from the body by one space.
        * Contains the reference to related issues, commits, requests, mails,
          people, etc.
        * No more than 80 characters.

## Find your git model

There are a huge amount of ways how you can organize your life with git but
I'll explore two very simple and commonly used.

### Git only model

* Each team member writes very informative and understandable commit messages.
* Each commit may contain some reference to the external discussions: mailing
  lists, bugzilla (optional).

Example:

```
Use -filelist with macOS linker

macOS's linker can take a -filelist argument, in place of taking the
list of object files to link on the command line. This is a more limited
version of "response files" as used elsewhere in the code base, and by
using it we make it far less likely that a linker invocation will hit
ARG_MAX.

The changes I've made to use -filelist are adapted from the code
elsewhere in gbuild that creates response files, but this is slightly
different because -filelist files are a bit different - they can only
contain object files, as opposed to arbitrary linker arguments, and
arguments are separated by newlines rather than spaces.

[1]: https://somereference

Reviewed-by: FooMan
```

### Mixed Model (Git + Bugzilla + Mailing Lists)

* Each team member writes very short and understandable messages.
* Each commit message contains a link to the issue tracker.

Example:

```
Use -filelist with macOS linker

Relates: #tdf83
Resolves: #tdf299
```

I mostly prefer to use the mixed model. It's very great to see the long
commit messages with a lot of tech details and interesting things but
usually it's hard to put all info into one commit message because of
different discussions in ML (mailing list), issue tracker, etc.

## Not all have to be masters

There is a cargo cult in some company that all changes must be pushed to the
main line only after +2 review points. In another companies developers don't
care and just push changes directly to the main line because it's easier
and they are used to do so. I want to briefly explore pros and cons of
these approaches.

### All are masters

* Usually people don't reread the changes. They make a patch, test it and
  push it to the main line.
* The codebase probably has some kind of smell because all are masters and
  only one approach of solving a problem or designing a system can be
  right - our own.
* It's fast because we don't spend time for reviewing other changes.
* It's fast because we don't need to wait until somebody will review us.

### There are only several masters

* Young developers learn how to write clean and simple code from the more
  experienced developers.
* Each commit message takes more time to write.
* Each changes takes more time before being merged into the main line.
* Procedure of code rereading before merging it allows to fix some typos,
  simplify things, remove debug messages.

## Instead of conclusion

There are a lot of discussions, cargo cults around successful git models.
I just analyze some approaches from the previous experience of working in
different companies and contributing to various open-source projects.
I enforce that all changes must be reviewed before merging to the
main line. But is is my rule and you can be probably very happy without
this annoying review. Try different approaches and find which of them
is more suitable for your team.

I don't provide the complete template of "good commit message" because
there are resources that did it for me. I'd highly recommend you to
read [Linus rules for commit messages](https://github.com/torvalds/subsurface-for-dirk/blob/a48494d2fbed58c751e9b7e8fbff88582f9b2d02/README#L88) and [Why commit
message is so important](https://chris.beams.io/posts/git-commit/).

After all, all you have left from the developer is a commit message. And when
bad days come I hope this message will help you to solve the most annoying
bug.
