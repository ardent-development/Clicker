/*** Clicker 3.0 **************************************************************\
 * Author:       twisted_nematic57                                            *
 * Date:         11/23/2024 [MM-DD-YYYY]                                      *
 * License:      GNU GPLv3 (or later) - see LICENSE                           *
 * Product Type: BASIC program                                                *
 * Platform:     TI-89 Titanium - can be ported to other Motorola 68000-based *
                                  TI calculators with ease.                   *
\******************************************************************************/

Clicker is a BASIC program that enables you to perform repetitive calculations
on your TI-89 Titanium much quicker than you can on the Home Screen. You can
even store and later access intermediate calculation results just as you'd be
able to do on the real Home Screen. It only has one assembly subprogram
dependency.

It works on the basis of performing _iterations_: a user-defined operation works
on a user-defined starting value. Then, the output of the operation is used as
input for the next iteration.

The program works flawlessly on negative and complex numbers. It can operate on
entire lists or matrices on a per-iteration basis. It has been tested on many
hundreds of inputs, and produces expected results every single time.

In summary, this program is one of the only and best dedicated recursive
function executors for any calculator out there. It is a stair step towards
putting your TI-89 Titanium right up there with Mathematica and MATLAB. As
always, it's up to you to harness its full potential.

  - created and refined with passion.


I. QUICK START

1. Install:
    - Transfer `clicker.89p` and `flib.89z` to your calculator.
    - Archive them for safety (optional but recommended).
2. Run:
    - On the Home Screen, type:
        `clicker(start_val, "operation", "listname")`
      Example: `clicker(0, "x+1", "")`
    - Press [ENTER] to iterate (count up from 0 in steps of 1), and [CLEAR] to
      quit the program.
3. Results:
    - The last iteration's result is saved to the `lastclic` variable. A list of
      all iteration results is not created.
    - For troubleshooting, ensure all inputs are properly formatted and make
      mathematical sense.

The sections below will take you through a more detailed, thorough explanation
of the program and its behavior.


II. INSTALLATION

Send `clicker.89p` to your calculator.
 It will be in its own folder "AAA" for quick access, but you can put it
   anywhere you like. It is folder-agnostic and can be called from anywhere.
 I recommend keeping it archived.
 It is GPLv3-or-later licensed, so if you wish to take advantage of the rights
   that implies then feel free to unarchive the variable and do whatever.

Send `flib.89z` to your calculator.
 It *MUST* be stored in the "main" folder.
 I recommend keeping it archived.
 It is GPLv2-or-later licensed, so if you wish to view its source code you can
   unzip "flibsrc.zip" and have at it.


III. DETAILS

 * Clicker does not use many graphical effects. It is quite lightweight on its
   own.
 * It works by executing an operation using a starting value as initial input.
    - Think of the operation as a function of `x`. `op(x)` = {your operation}
    - When you press [ENTER], your starting value is plugged into `op(x)`. The
      result is then stored to `x`, and displayed on the screen.
    - As you keep pressing [ENTER], `op(x)` will be executed and its result
      stored to `x`, over and over again. It's essentially recursively executing
      the operation with its own previous output every time you press [ENTER].
 * You may press [CLEAR] to exit the program and go back to the Home Screen at
   any time.
 * Clicker will store your calculation history to a list or sequence of
   variables of your choice, if you tell it to do so.
    - Iteration numbers are 1-indexed, both when saving to a list and to a
      series of variables.
 * If any issues happen during execution of the program, it will catch most of
   those errors and let you know what's wrong. In fact they are not called
   "errors"; instead they are called "oopsies" since that's more friendly and
   less robotic than the word "error".
    - If there is an error during calculation, then it is highly likely that the
      issue lies in your `x` or `op`. For example, trying to do things with
      non-square matrices can often upset the calculator.


IV. USAGE

 * At the Home Screen, invoke Clicker with 3 arguments, in this order:
    - `x`: An expression that will be initially plugged into op(x). Can be
           any kind of number (positive, negative, complex, etc.), or a
           matrix/list.
    - `op`: A string containing any function of `x`.
             ~ Other variables may be included in the function, as long as they
               are defined beforehand (in most cases).
             ~ Unfortunately it is not possible to chain commands using the `:`
               character.
    - `calclist`: A string containing the name of the list that the calculation
                  history should be stored to upon exit.
                   ~ If set to 0 or an empty string (`""`), only the last result
                     of the final iteration is stored to a variable named
                     `lastclic` in the current folder. Every iteration result
                     that came before it is discarded.
                   ~ The list name must not start with a number, it must not
                     contain a space character, and its length must be between 1
                     and 8.
                   ~ Recording data to a list can be especially slow after
                     a couple dozen iterations. Do not use this feature in
                     performance-critical scenarios.
                      ~ Due to the inherent loss of performance caused by the
                        data recording routines, there is a QoL feature only
                        active in iteration-recording mode that displays the
                        current iteration number in the status line. This
                        feature was technically too slow to implement in
                        non-recording mode, but it really didn't hurt this one
                        where operations are already slower than instantaneous.
                   ~ If `x` or `op` contains a list or matrix in itself, the
                     calculation history cannot be stored to a list. Instead, it
                     will be stored to a series of variables with a prefix
                     matching the first 4 characters of the `calclist` string
                     followed by a fixed-length, 4-digit, base-10 integer
                     denoting the iteration number.
                      ~ For example, assuming `x` and `op` contain lists within
                        themselves, and `calclist` is set to "history", then the
                        result of the first iteration will be stored to
                        `clkrvars\hist0001`, the second to `clkrvars\hist0002`,
                        etc.
                      ~ If the calculator runs out of RAM while doing
                        iterations when saving to individual variables, then the
                        program will not catch this error and you will need to
                        exit it by pressing the [ON] key. However, if you
                        archive the old iterations, set your `x` to the result
                        of the last iteration, and change some part of
                        `calclist`, you could essentially continue from where
                        you left when RAM ran out.
 * The calc will switch to the PrgmIO screen and display "Ready." Now, whenever
   you press [ENTER], the current value of `x` will be plugged into the
   operation you specified, and its result stored to `x`.
 * Upon pressing [CLEAR], the program will return to the Home Screen, save the
   calculation history to a list if specified, and terminate.

DISCLAIMER: Treating the program in ways that deviate from the specification
above may cause unexpected and erratic behavior. No damage should ever occur to
your calculator by using this program, but the author(s) of this program do not
claim liability for ANYTHING should undesirable events occur as a result of the
distribution, storage, compression, or execution of this program.


V. EXAMPLES

 1. `clicker(0,"x+1",0)`: The first press of [ENTER] will display a 1. Pressing
                          it repeatedly will count upwards. The calculation
                          history will be discarded upon program termination.

 2. `clicker(2,"x^2","pow2")`: The first press of [ENTER] will display a 4.
                               Pressing it repeatedly will display successively
                               larger powers of 2. The calculation history will
                               be stored to a list named `pow2`.

 3. `clicker(0,"x^2+c","mandel")`: Repeatedly pressing [ENTER] will quickly
                                   reveal if the complex number in `c` is part
                                   of the Mandelbrot Set. Calculation history
                                   will be stored to a list named `mandel`.
 4. `clicker({2/3,3,5,7},"root(x,3)","cbrts")`: Gets the cube roots of 2/3, 3,
                                                5, and 7; stores the results of
                                                each iteration to a series of
                                                variables in the folder
                                                "clkrvars"
 5. `clicker([[5,3][8,2]],"x^4","mat")`: Gets the 4th power of the matrix, and
                                         stores the results of each iteration to
                                         a series of variables in the folder
                                         "clkrvars"

Screen recordings showing the above examples are in the "demos" directory.
Please keep in mind that the calculator shown in the videos is emulated and is
a bit less responsive to rapid input than the physical TI-89 Titanium.


VI. CHANGELOG (LATEST-FIRST)

 * Clicker 3.0: Guarantees ability to work with lists and matrices; Takes
                advantage of the status line; Adds input validation; Many
                documentation improvements
    - CODE: Add descriptive error dialogs to indicate invalid input.
    - CODE: More intuitive handling of error dialog input
    - CODE: Leverage the status bar to display relevant information (requiring
            use of flib)
       ~ Unfortunately BASIC is too slow to show the current iteration number in
         the status line in a performant manner. For this reason it is only
         implemented in the data-recording mode, as that is already slow to
         begin with.
    - CODE/DOC: Guarantee support for calculation involving lists and matrices
    - DOC: Add more information about handling of `op` and `x`
    - DOC: Improve formatting, break up text walls into digestible paragraphs
       ~ Not perfect, but I tried :/
    - DOC: Add a "QUICK START" section for newbies
    - DOC: Add more examples involving lists and matrices
    - DOC: Number the examples, add screen recordings

 * Clicker 2.0: Adds ability to save calculation history to a list
    - CODE: Add functionality to keep track of clicking history in a list
       ~ Due to the (relatively) performance-critical nature of this code, some
         code duplication has taken place to enhance processing speed during
         execution of the program.
    - DOC: Reformat header, clarify some minor details
    - DOC: Update documentation to reflect changes in the code
    - DOC: Add one more example and update previous ones to align with the new
           version of the program's requirements

 * Clicker 1.0: Initial release just has the ability to recursively perform an
                operation on a variable and discard everything at termination.
