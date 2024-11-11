/*** Clicker 1.0 **************************************************************\
 * Author: twisted_nematic57                                                  *
 * Date: 11/11/2024 [MM-DD-YYYY]                                              *
 * License: Public Domain :)                                                  *
 * Product Type: TI-89 Titanium BASIC program                                 *
\******************************************************************************/

Clicker is a very simple BASIC program that enables you to perform repetitive
tasks on your TI-89 Titanium much quicker than you can on the Home Screen.

I created this program because I often use my calculator to count large numbers
of things to guarantee the lack of human error. However, especially if my
calculation history is populated, I find that repeatedly pressing the Enter key
when doing `ans(1)+1` is not ideal, since the calculator will "miss" a couple
counts while "processing" previous ones. It is very annoying, and I hate having
to pull out my 36X Pro for anything.


I. INSTALLATION

Send clicker.89p to your calculator. It will be in its own folder "AAA" for
 quick access, but you can put it anywhere you like. I recommend keeping it
 archived.


II. DETAILS

 * Clicker is purely a TUI program.
 * To work it, you have to pass a starting value and an operation.
    - Think of the operation as a function of `x`. op(x) = {your operation}
    - When you press Enter, your starting value is plugged into op(x). The
      result is then stored to `x`, and displayed on the screen.
    - As you keep pressing Enter, op(x) will be executed and its result stored
      to `x`, over and over again. It's essentially recursively executing the
      operation with its own previous output every time you press Enter.
 * You may press [CLEAR] to exit the program and go back to the Home Screen at
   any time.


III. USAGE

 * Please make sure the variable `x` is undefined.
 * At the Home Screen, invoke Clicker with two arguments, in this order:
    - `x`: A number specifying the initial value to be plugged into op(x).
    - `op`: A string containing any function of `x`.
 * The calc will switch to the PrgmIO screen and display "Ready." Now, whenever
   you press Enter, the current value of `x` will be plugged into the operation
   you specified, and its result stored to `x`.


IV. EXAMPLES

 * `clicker(0,"x+1")`: The first press of Enter will display a 1. Pressing it
                       repeatedly will count upwards.
 * `clicker(2,"x^2")`: The first press of Enter will display a 4. Pressing it
                       repeatedly will display successively larger powers of 2.
