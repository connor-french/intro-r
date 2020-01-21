Introduction
================

[\<\<\< Previous](../README.md) | [Next \>\>\>](02-functions.md)

-----

> ## Learning Objectives
> 
>   - Describe the purpose of RStudio’s script, console, environment,
>     and file/plot/help windows.
>   - Create an R project.
>   - Organize files and directories for a set of analyses as an R
>     Project.
>   - Use the built-in RStudio help interface to search for more
>     information on R functions.

-----

# Basics of R

R is a versatile, open source programming/scripting language that’s
useful both for statistics but also data science.

  - **Open source** software under GPL.
  - R has over 7,000 user contributed packages at this time. It’s widely
    used both in academia and industry.
  - Available on all platforms.
  - Not just for statistics, but also general purpose programming.
  - For people who have experience in programmming: R is both an
    object-oriented and a so-called [functional
    language](http://adv-r.had.co.nz/Functional-programming.html)
  - Large and growing community of peers.
  - You can use R as it is but combining it with the RStudio interface
    will help with organization and also provide us with extra options.

# Presentation of RStudio

Start RStudio – Let’s start by learning about our tool.

  - Console, Scripts, Environments, Plots
  - Code and workflow are more reproducible if we can document
    everything that we do.
  - Our end goal is not just to “do stuff” but to do it in a way that
    anyone can easily and exactly replicate our workflow and results.

## RStudio layout

Let’s learn where things are and what we can do\!

  - How do you a) open a new R script window?
  - How do you b) search for the documentation of the function `sum`?

![The console, scripts, environment, and plots windows on
RStudio](https://github.com/connor-french/intro-r/blob/master/images/RStudioLayout.png)

  - Bottom left: **console window.** Here is where R is waiting for you
    to tell it what to do, and where it will show the results of a
    command. You can type commands directly after the “\>” prompt and R
    will execute the command. Commands written in this window will be
    forgotten after you close the RStudio session.

  - Top left: **scripts/editor window.** In this R script window, you
    can write, edit, and save your R commands. Here you can have a
    complete record of what you did, and you can easily share with
    others how you did it and you can do it again later on if needed.
    The RStudio script editor allows you to ‘send’ the current line or
    the currently selected text to the R console for execution by
    clicking `Run` or by using the `Command-Enter` (for MacOS) or
    `Ctrl-Enter` (for PCs) shortcuts. You can also run the full R
    script.

  - Top right: **environment/workspace/history window.** Here you can
    see what data and values R has in its memory. You can view and edit
    these values by clicking on them. In the history tab, it shows you
    what you have typed before.

  - Bottom right: **files/plots/packages/help window.** The files tab
    shows you your current working directory’s file and folder
    structure. The is usually where your project file is saved. The
    plots tab will show you resulting graphs/figures that you execute.
    The packages tab will list all the packages that are installed. If
    the package is loaded, a check-mark will appear next to it. The help
    tab will show you the documentation for the R functions, datasets,
    and packages which is helpful for when you come across code that you
    aren’t sure about.

# Before we get started

  - Under the `File` menu, click on `New project`, choose `New
    directory`, then `New/Empty project`
  - Enter a name for this new folder, and choose a convenient location
    for it. This will be your **working directory** for the rest of the
    day (e.g., `~/intro-r`)
  - Confirm that the folder named in the `Create project as a
    sub-directory of` box is where you want the working directory
    created. Use the `Browse` button to navigate folders if changes are
    needed.
  - Click on “Create project”
  - In your console (window on the bottom left), first make sure that
    you’re in your `~/intro-r` directory. If not, navigate there. Then,
    create a folder named `data` within your newly created working
    directory. (e.g., `~/intro-r/data`)
  - Create a new R script (File \> New File \> R script) and save it in
    your working directory (e.g. `intro-r-script.R`)

Your working directory should now look like this:

![How it should look at the beginning of this
lesson](../images/r_starting_how_it_should_like.png)

# Interacting with R

There are two main ways of interacting with R: using the console or by
using script files (plain text files that contain your code).

If R is ready to accept commands, the R console shows a `>` prompt. If
it receives a command, R will try to execute it, and when ready, show
the results and come back with a new `>` prompt to wait for new
commands.

If R is still waiting for you to enter more data because it isn’t
complete yet, the console will show a `+` prompt. It means that you
haven’t finished entering a complete command. This is because you have
not ‘closed’ a parenthesis or quotation. If you’re in Rstudio and this
happens, click inside the console window and press <kbd>Esc</kbd> or
`Ctrl-C`; this should help you out of trouble.

Try entering this into your console:

``` r
(3 + 3
```

Your console chould look like this:

![](../images/unclosed-parentheses.png)

If you keep pressing enter, more `+` will appear. To fix this, close the
parentheses with `)` to evaluate the expression, or <kbd>Esc</kbd> or
`Ctrl-C` to escape and leave the expression unevaluated.

## Using script files

One of the highlights of RStudio is the text editor. It contains a lot
of handy features that make coding easier. For now, we’ll just use some
basic features.

Let’s open a new R script. In the top left corner of your RStudio
window, there should be a paper icon with a green plus sign over it.
Click on it and select “R Script” from the dropdown menu. A new blank
script should appear in your top left pane. This is essentially a text
file, but since it has a “.R” extension, you can use it to “talk” to
your R console. What I mean is that instead of typing commands directly
into the console or copying and pasting, you can run code directly from
the script.

A nice feature of R is that it is interactive. You can run a single line
of code at time without needing to run the entire script.

Lets do some math in your script. Type `3 + 3` into your R script. Place
your cursor at the end of the line and press
<kbd>Cmd</kbd>-<kbd>Enter</kbd> (<kbd>Ctrl</kbd>-<kbd>Enter</kbd> if you
have a Windows). You should now see the output in your R console\! If
you want to run more than one line of code, you can highlight the code
you want to run and press <kbd>Cmd</kbd>-<kbd>Enter</kbd>.

Now, let’s save our script with File -\> Save or File -\> Save As. R
should default to your working directory. Save it wherever the .RProj
file is located.

Now, quit your RStudio session. You may be confronted with a message
that asks “Save Workspace Image?” ALWAYS SAY NO. It will create
headaches if you save it. It takes forever if you have a lot of stuff in
your environment and writes all of your objects to disk. While saving
everything you’re working with may sound like a good idea, but you’re
now responsible for remembering what each file is for. Also, what R
saves may not actually reflect what was in your environment. Just
suffice it to say that saving your workspace image is a bad idea.

We’re gonna learn how to open your R project again. There are two
avenues:

1)  Double click your .RProj file. This will open your R project in a
    new window and everything will be there ready to go.

2)  Open RStudio. RStudio may automatically open your most recent
    project. In that case, you don’t have to do anything. Otherwise, go
    to File -\> Open Project and navigate to your .RProj file. Open this
    and you’ll be good to go\!

Note: Don’t just double click the .R file or open the .R file in RStudio
without opening your .RProj first. If you don’t open your R Project,
things may break.

-----

[\<\<\< Previous](../README.md) | [Next \>\>\>](02-functions.md)  
[Glossary](glossary.md)

-----

**Note**: The introductory material is copied and modified from [Data
Carpentry](http://datacarpentry.org).
<http://creativecommons.org/licenses/by/3.0/>. “Copyright (c) Data
Carpentry”
