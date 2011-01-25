# ant-el: [Emacs][0] things for [ant][1]

By Andrew Gwozdziewycz, licensed under the [GNU GPLv3][2]

This is a few helpers for using compilation mode in Emacs with ant.

### Customizations

If your ant is in a nonstandard location, `(setq ant-command "/path/to/ant -emacs")`

If your build doesn't use "build.xml", you'll need to end `ant-command` with `-buildfile` or `-file` and also do `(setq ant-build-file-name "somethingelse.xml")` so that the automated project root discovery works correctly.

### Installation

Put ant.el in your `load-path` and add `(require 'ant)` to your .emacs

### Usage

The basic operation is to invoke `M-x ant`, which will ask you for a task to perform, using a completing read based on the defined targets in your build file.

`M-x ant-last` will re-issue the last command

`M-x ant-compile` will run the standard `ant compile`

`M-x ant-clean` will run the standard `ant clean`

`M-x ant-test` will run the standard `ant test`

`ant` can be called non-interactively too, in which case it's called as such: `(ant "sometask")`. This means that you can can define your own functions like `ant-compile` for your projects:

    (defun ant-compile-full ()
        (interactive)
        (ant "compile_full"))
        
`M-x ant-kill-cache` kills the internal cache used to speed up the auto-completion of ant tasks in the mini-buffer.
        

[0]: http://gnu.org/software/emacs
[1]: http://ant.apache.org
[2]: http://www.gnu.org/licenses/gpl.html
