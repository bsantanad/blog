# brief introduction to git for solo developers

I've been using `git` for a while now and I know that at first it can be
overwhelming. `git` is wild beast, you can do a lot of stuff with it.
Nevertheless after using it for a while you'll realise that you wont be using
all git capabilities on a daily basis, just the basic ones. Those are the ones
that I'll try to cover in this blog post.

I will explain them the way I would have like to have them explained to me
when I was starting, but, hey, you are not me, so your mileage may vary.

## what is git?

`git` is a version control system. This means it will help you keep track of
the versions of your code. 

Let's see an example, say you just finished an assignment for your _Coding in
C_ class. You are just reviewing the requirements and checking all the boxes.
When all of the sudden you come across one you haven't seen before. Its not the
end of the world, you realise it's just a simple feature that you will be able
to add in no time.

So you open your favourite text editor and start modifying the code. You
finish, it looks pretty good. Let's compile it then. Perfect. Now let's test
it.  Oops, _Segmentation fault (core dumped)_. "Damn" you think "is this a new
error?", "was this showing up before I made the last changes?", "what did I
changed?", "I did not modify the core functionality, did I", "is there a way I
can go back in time to when it worked?".

If this ever happened to you, then the way you "go back in time" is by using
`git`. `git` let us create snapshots of the current state of the project,
meaning we can go back to a state of the project where it actually worked or
where we had not made something stupid.

It will help you a lot, even if you are working alone.

## using git 

Going back to the example of your _C assignment_, say you knew how to use git
before starting to code. So the first step you did was create the directory
where the code will be placed, `cd` into it, and do:
```
git init
```
This will initialise git (if the command was not obvious enough). It will
create a hidden directory `.git` but what happens inside there is a story for
another day.

Cool, so now you have `git` initialised in your directory, now you start coding
and have the first version you want to keep track of, like a good checkpoint to
have if everything goes bananas. How do I start taking snapshots?  First we
have to say which files we want to keep track of. Say your directory looks like
this:
```
.
├── main.c
├── lib.c
└── lib.h
└── trash 
```
We do not want to keep track of the trash file right? So we will **add** the
files we want to track with the `git add` command.
```
git add main.c
git add lib.c lib.h
```
You can do `git status` at anytime to check what are you doing, in this case
it will tell you the following:
```
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   file.c
        new file:   file.h
        new file:   main.c

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        trash

```
Is the snapshot taken yet? nope. I like to make the analogy of you taking
copies of a physical document, you go to the copy machine, put the paper in the
machine and then press the button right? Well we are in that first step of
going to the machine and putting the paper. We still have to press the button.

Now let's create the snapshot then.
```
git commit -m "first commit"
```
We can use the `git commit` subcommand for that. To be honest I don't like the
`-m` argument, I prefer to do:
```
git commit -vs
```
This will sign `-s` the commit with your name (commit is the git name for what
we have been referring to as a snapshot), telling everyone that you made it
(for better or for worse), and will open a text editor `-v`. There you will be
able to write the commit description.

This descriptions have a title and a body, something like this:
```
first commit, basic functionality working

main.c and lib.c are linked with the header file, this helps
the functions inside lib.c to be used in main. main.c has ....

# more text

Signed-off-by: dostoyevski crime@punishment.com

# changes done 
```
This description and title will help anyone who wonders what does that commit
adds or removes (including you). If you scroll down you can see the changes you
made.

If you do `git status` again you'll just see the trash file:
```
$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        trash

nothing added to commit but untracked files present (use "git add" to track)
```
and if you do `git log` you'll see the commit you just made
```
$ git log
commit c90ae394e0dd13cfbedddbeb69825d051e4d01ce (HEAD -> master)
Author: dostoyevski crime@punishment.com
Date:   Sat May 14 17:49:34 2022 -0500

    first commit, basic functionality working

    main.c and lib.c are linked with the header file, this helps
    the functions inside lib.c to be used in main. main.c has ....

    # more text

    Signed-off-by: dostoyevski crime@punishment.com
```

Let's sum up.

- `git init`: initialise git in a directory
- `git status`: check what are we doing with git (the state of the repo) 
- `git add <somefile>`: add a file to the stage env (like placing the paper in
  the copy machine)
- `git commit -vs`: take the snapshot, sign it, and document it (like pressing
  the button in the copy machine)
- `git log`: check the history of commits (snapshots you have taken)

There is one last operation I want to cover in this post, `git diff`, this a
quite useful subcommand that helps us see what has changed form the previous
commit to the current state.

Say you made your commit and continue working. Now you reach another milestone
in your project so you think is a good time to take another snapshot. You
already know the workflow, so you do `git add main.c` then `git commit -vs` you
write the title and body, and you check the history with `git log`. But what if
you want to see what you are are about to commit? like see the actual changes
you did to the files. Then you do `git diff`, it will show you in red the lines
you removed, and on green the ones you added. Pretty cool right?

Well, as stated in the title, this is just a brief introduction, probably I
will write more posts on other git stuff that can help you with your workflow,
until then, take care.
