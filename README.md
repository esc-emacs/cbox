# cbox - comment blocks in boxes

*cbox now supports Emacs Lisp, C like languages and R. It can easily be adapted for any language. Currently the source code can be modified slightly to support your favorite language, however soon you can do this directly from your .emacs for practical reasons*

cbox allows the user to type in long comments explaining programs, putting in licenses
and describing large sections of source code. It does so by opening up a temporary buffer
for editing. Once finished the comment is inserted and boxed around for pretty
formatting. Comments generated by cbox can be edited once they have been inserted
by calling the same function that created them:
```
cbox-trigger
```

You can also edit the comments generated by cbox by moving your cursor on top and
calling `cbox-trigger` (or rather the key binding you mapped to it).

## How to install cbox
First of all, make sure that `cbox.el` is somewhere in your load path. As an example,
I put elisp files in a `lisp/` folder in `~/.emacs.d/`, obviously make sure you create
that directory with `mkdir ~/.emacs.d/lisp/` and make sure you put this in your `.emacs`
```lisp
;;; Add load path for lisp files
(add-to-list 'load-path "~/.emacs.d/lisp/")
```

Now, you need to make sure you load it when needed so put this in your `.emacs`
```lisp
(autoload 'cbox-trigger "cbox" "Comment blocks editing" t)
```

You need to map cbox-trigger to something you like, I like to use `C-c /'
```lisp
(global-set-key (kbd "C-c /") 'cbox-trigger)
```

## How to use cbox

Move the point (cursor) to where you want to put the comment block.

![image1](http://i.imgur.com/DPjjv1t.png)

Now type whatever key binding you mapped to cbox-trigger. In the example above we used `C-c /`.

![image2](http://i.imgur.com/x56c5xb.png)

A buffer should have opened.

![image3](http://i.imgur.com/JIYMCPF.png)

Now type your comment and type `C-c C-c` that should insert the text as a comment in
the original buffer.

![image4](http://i.imgur.com/7enVqNN.png)

## To finish

***You can abort*** typing a comment by doing `C-c C-k` in the `cbox edit` buffer.

***You can edit an existing comment*** by moving your point (cursor) on top of the
comment and typing the same keybing you mapped to `cbox-trigger` note that the comment
has to be in the same format that cbox uses to generate comments in order to edit it
