# learning Scheme using chicken implementation

here I'll keep the notes I make while learning to program in Scheme using
the [chicken][chicken] impl. These are for personal use, so if you stumble
on this by any chance excuse the mistakes and messiness.

## day 1

### backstory

I was "watching" a movie while scrolling through my phone checking hacker news
when I stumbled into [this post][post] that talked about a _hobby_ programming
lang with a syntax similar to lisp. I never learnt lisp in university and I had
not taken the time to learn more about it, but I was curious on how it worked.
Scrolling through the post comments, I found one that said it was just a Scheme
implementation.

Me, not knowing what they were talking about -- like, what is Scheme? -- decided
to google it to discover that is like lisp but more simple and minimal? (do not
quote me on that)

I started looking for resources to learn this Scheme programming lang. I
found a book called [the little schemer][book]. After reading some reviews
I realised I was not going to learn lisp or scheme with this book alone, but
that this book teaches you how to think in a way that makes you a better lisp
or scheme programmer. I started reading it, but soon realised I wanted to
run some Scheme code first and then come back to this book to improve on my
thinking.

This is where I stumbled with this [book][csutexas], it seems it's like for
a computer science class in the University of Texas? I don't know. Anyway, I
read the overview, and jumped into the _using scheme_ part.

First thing it mentioned is that you'll need a scheme implementation to follow
this book. I did not have any installed in my OpenBSD workstation. So I went
surfing the web looking for different options. After a quick search I soon
realised that there are a lot, but there were two that caught my attention
[chicken][chicken] and [guile][guile]. I choose the first one, installed it
in my system with `pkg_add chicken` (simple as that) and I was able to jump
into a interactive programming enviorment (the same thing as if you type
python in your terminal, like a shell) by typing `chicken-csi`, and then
the fun started :).

### actual notes

#### define things

you can do `chicken-csi` to start an interactive programming env. There you can
define variables and things like that. From what I've learned, there are
two main things in schemes, atoms and lists.

- hola is an atom
- (hola jose) is a list

To define a variable, you can do:
```
#;> (define number 10)
#;> number
10
```
then if you type `number` it will show the 10.
(I will just write `#;>` to symbolise the prompt.)

This is the way you define procedures too (I'm pretty sure a procedure is the
same as a function, but with diff name). Here's an example:
```
#;> (define (double n)
        (+ n n))
```
We are defining a procedure with the name `double` that receives 1 param `n`
then it adds `n + n` and returns it. Note that the operation is not in the way
we usually think of operations, instead the operator **precede** the operands.

Once I saw the notation I remember our Discrete Maths class, we saw this type
of notation, it is called [polish notation][wiki] and help us when you want
to build trees out of the operations. Anyway, back to chicken scheme.

#### booleans

we can write an if statement very easily.
```
(if (< 1 2)
    1
    2)
```

This is read as, if 1 is less than 2 return 1 else return 2, in python it
would look something like this:
```
if 1 < 2:
    return 1
return 2
```
there are special objects that represent true `#t` and false `#f` so if you
do:
```
#;> (< 2 3)
#t
```
You can see that it returns the true object.

Finally, let's see a procedure that uses an if statement.
```
(define (min_n a b)
    (if (< a b)
        a
        b))
```
now we can call it just by doing
```
#;> (min_n 10 2)
2
```
_NOTE_: any other value other than `#f` is considered true

I decided to stop there for the first day, hopefully I have time to continue
on learning Scheme in the next few days, I'm enjoying it quite a bit.

## day 2

to be continued... (hopefully soon)

[chicken]: https://wiki.call-cc.org/
[post]: https://news.ycombinator.com/item?id=31782985
[book]: https://mitpress.mit.edu/books/little-schemer-fourth-edition
[csutexas]: https://www.cs.utexas.edu/ftp/garbage/cs345/schintro-v14/schintro_toc.html
[guile]: https://www.gnu.org/software/guile/
[wiki]: https://en.wikipedia.org/wiki/Polish_notation
