# squashing commits in git

We've all been there, you just finished correcting all the typos of your README
or documentation, you have already made the commit, push the changes, and then
you realise you misspelled a word. "Damn" you think "do I have to make a new
commit for this small change?", "that will only make the history of the repo
bigger and messier". Good thing there is a way of fixing this.

Welcome to squashing commits. I am going to explain the way I do it, I don't
know if it's the best but it works perfectly for me, so it should work for you.

Say you have your history this way:
```
$ git log --abbrev-commit --pretty=oneline
9f0fd1c (HEAD -> master) anther typo i had not seen
5bc004b typo I missed
78cf95f fixing typos in README
773350e good commit
```
The `78cf95f` is the good one (the one we want to keep), `5bc004b` and
`9f0fd1c` are the ones we want to get rid off. Meaning it would be nice that
the last two commits could be _"merged"_ with `78cf95f` this way we would only
have one clean and simple commit for correcting typos.

What do we do? We can use the `rebase` subcommand to _squash_ the other two
commits under that one:
```
$ git rebase -i 78cf95f^ # please note the ^
```
After we run this a text editor will be open and this will be displayed:
```
pick 78cf95f fixing typos in README
pick 5bc004b typo I missed
pick 9f0fd1c anther typo i had not seen

# some comments
```
Then we can just squash the commits we want, so:
```
pick 78cf95f fixing typos in README
squash 5bc004b typo I missed # edit this line
squash 9f0fd1c anther typo i had not seen # edit this line

# some comments
```
We just need to rewrite `pick` -> `squash`. Then we are good to go, save and
quit your text editor.

The text editor will be opened again. This time we can modify the commit
messages, in case we want to add something, or just remove the message for the
two commits we are squashing. Once you are happy with the result, just save,
quit, and voila.
```
$ git log --abbrev-commit --pretty=oneline
0335a16 (HEAD -> master) fixing typos in README
773350e good commit
```

You now have a single, clean, commit. No need to contaminate your history with
unnecessary commits.

Hope this was helpful.

Thanks,

Ben

