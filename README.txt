/*** Clicker 2.0 **************************************************************\
 * Author:       twisted_nematic57                                            *
 * Date:         11/17/2024 [MM-DD-YYYY]                                      *
 * License:      CC0 :)                                                       *
 * Product Type: BASIC program                                                *
 * Platform:     TI-89 Titanium                                               *
\******************************************************************************/

Clicker is a very simple BASIC program that enables you to perform repetitive
tasks on your TI-89 Titanium much quicker than you can on the Home Screen.
Thanks to new features in v2.0, you can even store and later access intermediate
calculation results just as you'd be able to do on the real Home Screen!

I created this program because I often use my calculator to count large numbers
of things to guarantee the lack of human error. However, especially if my
calculation history is populated, I find that repeatedly pressing the [ENTER]
key when doing `ans(1)+1` is not ideal, since the calculator will "miss" a
couple counts while "processing" previous ones. It is very annoying, and I hate
having to pull out my 36X Pro for anything.

Ultimately, this program is just a fancy recursive function executor. You can
use it to count huge numbers and do other very repetitive tasks without filling
up your Home Screen with garbage.

  - with passion, twisted_nematic57


I. INSTALLATION

Send clicker.89p to your calculator. It will be in its own folder "AAA" for
 quick access, but you can put it anywhere you like. I recommend keeping it
 archived.


II. DETAILS

 * Clicker is purely a TUI program.
 * It works by executing an operation on a starting value.
    - Think of the operation as a function of `x`. `op(x)` = {your operation}
    - When you press [ENTER], your starting value is plugged into `op(x)`. The
      result is then stored to `x`, and displayed on the screen.
    - As you keep pressing [ENTER], `op(x)` will be executed and its result
      stored to `x`, over and over again. It's essentially recursively executing
      the operation with its own previous output every time you press [ENTER].
 * You may press [CLEAR] to exit the program and go back to the Home Screen at
   any time.
 * Clicker will store your calculation history to a list of your choice, if you
   tell it to do so.


III. USAGE

 * At the Home Screen, invoke Clicker with 3 arguments, in this order:
    - `x`: A number specifying the initial value to be plugged into op(x). Can
           be negative, complex, whatever.
    - `op`: A string containing any function of `x`.
    - `calclist`: A string containing the name of the list that the calculation
                  history should be stored to upon exit. It must not start with
                  a number, it must not contain a space character, and its
                  length must be between 1 and 8. If this is set to 0 (integer),
                  then calculation history will not be recorded at all.
 * The calc will switch to the PrgmIO screen and display "Ready." Now, whenever
   you press [ENTER], the current value of `x` will be plugged into the
   operation you specified, and its result stored to `x`.
 * Upon pressing [CLEAR], the program will return to the Home Screen, save the
   calculation history to a list if specified, and terminate.
    - Keep in mind the calculator starts to lag a bit and respond more slowly to
      quicker presses of the [ENTER] key when the length of the list reaches ~80
      or so.

Treating the program in ways that deviate from the specification above may cause
unexpected and erratic behavior. No damage should occur to your calculator by
using this program, but I do not claim liability for ANYTHING should undesirable
events occur as a result of the execution, storage, transmission, or reception
of this program.


IV. EXAMPLES

 * `clicker(0,"x+1",0)`: The first press of [ENTER] will display a 1. Pressing
                         it repeatedly will count upwards. The calculation
                         history will be discarded upon program termination.

 * `clicker(2,"x^2","pow2")`: The first press of [ENTER] will display a 4.
                              Pressing it repeatedly will display successively
                              larger powers of 2. The calculation history will
                              be stored to a list named `pow2`.

 * `clicker(0,"x^2+c","mandel")`: Repeatedly pressing [ENTER] will quickly
                                  reveal if the complex number in `c` is part of
                                  the Mandelbrot Set. Calculation history will
                                  be stored to a list named `mandel`.


V. CHANGELOG (LATEST-FIRST)

 * Clicker 2.0: Adds ability to save calculation history to a list
    - CODE: Add functionality to keep track of clicking history in a list
       - Due to the (relatively) performance-critical nature of this code, some
         code duplication has taken place to enhance processing speed during
         execution of the program.
    - DOC: Reformat header, clarify some minor details
    - DOC: Update documentation to reflect changes in the code
    - DOC: Add one more example and update previous ones to align with the new
           version of the program's requirements

 * Clicker 1.0: Initial release
