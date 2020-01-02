## Original Author - [Nick Janetakis](https://nickjanetakis.com/)
@Repo [nickjj/notes](https://github.com/nickjj/notes)


# Notes

A small and simple shell script for text notes managment.

Instead of trying to impose a whole bunch of rules and syntax requirements,
this tool does its best to get out of your way.

It tries to do everything possible so that if you're working in a terminal, you
can save whatever text you want into a file. This could come from typing a
sentence out, pasting something from your clipboard or saving the output of a
program.

## Why have I started using it?

I have been using notepad++, and OneNote for a long time now as of 2019.
On Linux, there is no tool worth a salt of OneNote. And majorly I was hoping
for a way or tool that would let me store my notes.

Many of times I did lost my notepad++ buffers (you do not require to save),
and almost always I have my notes littered all over places.

This nifty script by Nick, is surely going to replace notepad++ use case.
That means not worrying about specific file types, formatting, tagging,
check boxes, syntax rules and a bunch of other things that delay you from
getting something out of your head and into a document.

## Text is amazing for notes because:

- You can use `grep` and friends to search through it later
- Even with notes dating back from 2001, I'm only using 1.5mb of disk space
- It's really easy to back up and sync to other devices using Drop Box or similar tools

I will be using it as a scattered brain dump. Even with things being very
unstructured (and even untagged) I can usually `grep` out anything I want
within a few seconds.

## Your notes are organized by auto-dated files

Let's say It's December 25th, 2019. If you were to run `notes hello world` it
would create a `2019-12-25.txt` file in your `NOTES_DIRECTORY` (this is
something you can configure). It would then append `hello world` to the end of
the file.

If you run `notes something else that is important` on the same day it would
continue to append to that file.

Daily notes gets combined and creates a monthly note file in format like `2019-12.txt`.


## What is this script not good for?

Depending on how you work, it's probably not ideal for grouping up a bunch of
extended thoughts about a specific topic.

For example, if you were planning to write a book and you spent 3 months
gathering info about what you're writing about then you would end up with a
bunch of isolated date formatted files that was mixed in with everything else.

In those cases, I recommend you use a simlar script called `book` which basically
does what this script does except it always dumps everything to 1 specific file
of your choosing which isn't dated. That's what I Nick says he do to help plan his
video courses.

## Installation

```sh
sudo curl \
  -L https://raw.githubusercontent.com/pskpatil/notes/master/notes \
  -o /usr/local/bin/notes && sudo chmod +x /usr/local/bin/notes
```

## Configuration

The first thing you'll want to do is configure where you want your notes to be
created. Also you may want to set EDITOR as a good practise.

```.bashrc
export NOTES_DIRECTORY="/tmp/foo"
export EDITOR=vim
```

If not set, value of `NOTES_DIRECTORY` is `${HOME}/notes`, and `EDITOR` is assumed to be `vi`.

Over WSL, it is suggested to keep NOTES_DIRECTORY to path like `/d/notes`.
As this will not require you to know `$HOME` location, in case of accessing outside WSL.


## Usage Examples

There's 3 ways of using this script:

- `notes something you want to jot down`
  - Appends whatever arguments you add as text into the dated file

- `xclip -o | notes`
  - Pipes and appends anything (in this case your clipboard's contents) into the dated file

- `notes`
  - Opens the dated file in your configured `EDITOR`

- `notes -h|--help`
  - -h shall be only argument to see usage.


### To-Do
1. book script
2. password (vim -x) # may be good for book