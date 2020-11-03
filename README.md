# Run-REDUCE-FX

## A JavaFX GUI to run any CLI version of the REDUCE Computer Algebra System

### Francis Wright, November 2020

Run-REDUCE-FX is a re-implementation of
[Run-REDUCE](https://fjwright.github.io/Run-REDUCE/) using JavaFX
instead of Swing.  The latest version of Run-REDUCE-FX requires Java
11 or later plus JavaFX 11 or later.

For further general background information please see the
[Run-REDUCE-FX web page](https://fjwright.github.io/Run-REDUCE-FX/).
For information about how to install and run Run-REDUCE-FX please see
the [Install and Run
Guide](https://fjwright.github.io/Run-REDUCE-FX/InstallAndRun.html).
For information about how to use Run-REDUCE-FX please see the [User
Guide](https://fjwright.github.io/Run-REDUCE-FX/UserGuide.html) (which
is also included in Run-REDUCE-FX and easily accessible via the Help
menu).

Run-REDUCE-FX should run on any platform that supports JavaFX 11 (or
later), but I can only test it on Microsoft Windows and Linux.
(Whilst Java is portable, filesystem structures, installation
conventions and display systems are not!)

REDUCE itself is an open source project available from
[SourceForge](https://sourceforge.net/projects/reduce-algebra/).  I'm
releasing Run-REDUCE-FX under the [BSD 2-Clause License](LICENSE),
mainly because it's the license used by REDUCE.

This project is set up for development using [IntelliJ
IDEA](https://www.jetbrains.com/idea/) with Run-REDUCE-FX as the
top-level directory.

Run-REDUCE-FX currently uses a bundled copy of
[KaTeX](https://katex.org/) to render LaTeX output by code based on
the REDUCE *tmprint* package when the *Typeset Maths* option is
selected.

## Release Notes

### Version 1.1

* Avoid warning messages and hanging Help menu items on Ubuntu, but
  suppress display of PDF files via the Help menu on non-Windows
  platforms since it's probably not currently very helpful!
* Add instructions for installing and running using Java 11 on Linux
  and improve the appearance of the User Guide.
* Use CSS to set the REDUCE font, size, weight and colour, and use the
  same font and size for input as well as output.
* Validate direct input to the FontSizeDialog via the editor.
* Validate generic root directories in REDUCEConfigDialog.  Rebuild
  the Run REDUCE submenus on saving REDUCEConfigDialog.  Improve error
  messages.

### Version 1.2

* Update the build environment to Java 11 and JavaFX 11, which are now
  also required to run Run-REDUCE-FX.
* Provide batch files to run Run-REDUCE-FX more easily.
* Re-instate display of PDF files via the Help menu on non-Windows
  platforms.
* Fix truncated text in the About dialogue.

### Version 1.3

* Provide templates for *df*, *int* and *mat* expressions and *for*
  statements.
* Add a hyperlinked Contents section to the User Guide.

### Version 1.4

* Provide templates for multiple integrals, finite sums and products,
  double- and single-sided limits, and solve.
* Provide a Functions menu offering dialogues that facilitate access
  to key elementary functions, Gamma, Beta and related functions,
  integral functions, Airy, Bessel and related functions, Struve,
  Lommel, Kummer, Whittaker and spherical harmonic functions, and
  classical orthogonal polynomials.  Special function names link to
  the online NIST Digital Library of Mathematical Functions.
* Appropriate templates include a symbolic/numeric option and access
  to relevant REDUCE switches and packages.
* Provide a pop-up keyboard (currently only on template and function
  dialogues) for symbolic constants, Greek letters, elementary
  functions, trigonometric functions (using radians or degrees) and
  hyperbolic functions.  **Still need to arrange that the pop-up
  keyboard loads the trigd package as appropriate.**
* The function dialogues and pop-up keyboard together offer all the
  functions listed in section 7.2 Mathematical Functions of the REDUCE
  Manual plus degree versions of all trigonometric functions.

### Version 1.5

* Add REDUCE Manual hyperlinks to all template and function dialogues.
* Add Help menu items that open the REDUCE Web Site and SourceForge
  Project Site in the default browser.

### Version 1.6

* Use WebView to display REDUCE output, and update instructions and
  batch files for running Run-REDUCE-FX accordingly.
* Set the default Session Log filename to `session.log`.
* Turning bold prompts on and off now works retrospectively.
* Turning I/O colouring on and off now works retrospectively (as far
  as possible).

### Version 1.7

* Add experimental Typeset I/O option, currently hidden, to the View
  menu to use fmprint and KaTeX, which does not yet work reliably.
* Update the documentation to try to make it easier to access the
  latest jar.
* Redesign the REDUCE Configuration dialogue:
  - Replace Packages Root Directory with REDUCE Packages Directory.
  - Split Documentation Root Dir into REDUCE Manual Directory and
    REDUCE Primers Directory.
  - **The above two changes are not backwards compatible!**
  - Add Initial I/O Directory, which defaults to the user's home
    directory, as before.
  - Add a ContextMenu to implement key choices for Initial I/O
    Directory: Home Directory; Current Directory; Another Directory.

### Version 1.8

* The Typeset Maths View menu option enables typeset-style display of
  algebraic-mode output.  But beware that this is currently
  experimental and has a number of limitations.
* Rename Initial I/O Directory to REDUCE Working Directory in the
  REDUCE Configuration dialogue.  This now sets the initial directory
  for both REDUCE and the file selectors and defaults to the user's
  home directory.
* View options apply to each REDUCE panel independently, initialised
  from the last selected (and saved) values, and the redfront View
  option takes effect after the next prompt.
* A toggle button on each REDUCE panel hides the input editor.
* When split-pane view is enabled after startup, the new panel is
  active and a green dot at the top right shows which panel is
  selected.

### Version 1.9

* Detect question prompts correctly.
* Add a *Print Session Log...* item to the File menu, which prints the
  entire content of the I/O Display pane as it appears on screen.
* Fix the *Save Session Log...* code to output the TeX markup used to
  display typeset maths.
* Move *Load Packages...* to the *REDUCE* menu.
* Support the pop-up keyboard on the input editor and add a label
  "Control+Click for the Pop-Up Keyboard" with a tooltip to the top of
  the input editor and the bottom of each template dialogue.
* Handle more of the non-standard TeX markup generated by fmprint.

### Version 2.0

* Fix the display of big delimiters in typeset maths.
* Always insert parentheses when calling a function using the pop-up
  keyboard, rewrite ln to log and remove the space after sqrt.

### Version 2.1

* Remember the directory used in the filechooser.
* Always decode non-ASCII characters from the pop-up keyboard and from
  templates to their correct REDUCE or TeX names.
* Replace loading the fmprint package with inputting and compiling the
  new source file "rrprint.red" contained in the JAR file, which is
  based on "tmprint.red".
* Typeset maths improvements:
  * Apply the fix by Eberhard Shruefer so that order commands work.
  * Output identifiers in mathit instead of mathrm style.
  * Correct spacing of := and leading + and - signs.
  * Display a trailing multiplication sign but otherwise ignore
    multiplications.  (This may be too drastic.)
  * Support all trigonometric and hyperbolic functions and their
    inverses, and logb and log10.
  * Display the gamma function, but not the identifier gamma, using a
    capital Gamma.
  * Support the polygamma, iGamma, iBeta, dilog, Pochhammer and
    integral functions.
  * Support Airy and Hankel functions.
  * Support Struve, Lommel, Kummer, Whittaker and spherical harmonic
    functions, and the classical orthogonal polynomials.

### Version 2.2

* Remove the middle mouse button binding for the pop-up keyboard,
  since it clashes with the X Window primary paste gesture (although
  this is not supported).
* Scroll more reliably to the bottom of the REDUCE I/O display window.
* Add a Kill REDUCE item to the bottom of the REDUCE menu.  Display an
  information alert when REDUCE is killed and an error message if this
  may have failed.  Handle failure of REDUCE to start better and check
  that REDUCE is alive before trying to send it input.
* Improve alerts relating to printing.
* Display the version number on the title bar.
* Add new sections on Editing, Typeset Maths Display and Printing on
  Linux to the User Guide.
* Typeset maths improvements:
  * Restore compatibility with tmprint so that `excalc.tst` runs.
  * Use a narrow space to indicate multiplication (except at the end of
    a line) because with no space x*y is indistinguishable from xy.
  * Output strings as text rather than maths and identifiers using
    mathit.  Support the dfprint switch.
  * Treat trailing digits in an identifier (optionally preceded by \_)
    as a subscript.  Treat the final _ in an identifier as introducing
    a subscript if it is followed by (the name of) a single character.
    But as a special case, display body_bar as \bar{body} for a
    single-character body or \overline{body} for a multi-character
    body.
  * Ensure that operator identifiers are subscripted like non-operator
    identifiers.  Note that line breaking is thoroughly broken!
  * Display repart and impart as \Re and \Im.
  * Display matrices more readably by using \displaystyle for each
    element and increasing the row spacing to 1.5em.
* REDUCE Configuration Dialogue improvements:
  * Use \ as directory separator in the Windows default configuration.
  * Detect unreadable directories and files in more fields.
  * Substantial revision to fix some subtle misbehaviour.

### Updates since last release

* Set minimum size for the main window.  Allow space at the bottom of
  the main display so that the horizontal scroll bar does not obscure
  the prompt.
* v2.21 Make "Generic information for all REDUCE commands" fields all
  optional, resetting to defaults where appropriate.  Correct the
  behaviour to allow the REDUCE Root Directory text field to be empty,
  and to use the Command Root Directory if it is set.
* Add line breaking support to the new code for displaying
  identifiers.
* Add support for conditional fancy!-functionsymbol properties that
  are association lists of pairs of the form `(arity . symbol)` and
  use it for the gamma function.
* v2.22 Fix fancy!-out!-item() so as not to hang the GUI if an error
  occurs and to output a more useful error message.
* Process _bar in an identifier as an over-bar even if it is followed
  by digits or _k.
* Set switch ACN on by default, since it seems to improve display with
  ON LIST.
* Add fancy!-assgnpri!-matrix() to display matrix assignments as
  assignments.
* Remove the declaration of fancy!-symbol!-length for setq and let it
  default to 4, which seems appropriate.  In fancy!-oprin, if `!*list`
  then break the line if `sumlevel!*` is 2 or 3; including 3 is a hack
  to fix the `on list` example in "alg.tst".
* v2.23 Use fancy!-functionsymbol rather than fancy!-special!-symbol
  for function names and set fancy!-symbol!-length as appropriate for
  function names.  Stop using `(ascii n)`, but retain support for it.
  Tidy up some of the functions for displaying special functions.
  This shortens some lines in `symbols_and_functions.tst` output.
* Display abs(x) as |x| and add abs to `symbols_and_functions.tst`.
* Display multiple matrix assignment correctly, e.g. `a := b :=
  mat(...)`.
* Use a character width of 2 instead of 1 in fancy!-tex!-character().
* Remove all superfluous space around commas in algebraic lists and
  flat printed matrix rows.
* Improve automatic scrolling to the bottom of the display pane.
* v2.24 Add a *Restart REDUCE* item to the REDUCE menu to do a full
  clean restart of the last-run REDUCE command.
* Give sqrt a width of 3 but remove the width of the n in an nth root.
  The output from "int.tst" is now reasonable.
* v2.25 Highlight warnings and errors with an appropriate background colour.
* Update UserGuide.
