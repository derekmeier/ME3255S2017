# Homework #2
## due 2/3/17

1. Now that you have created your own repository, 'homework_1', that has a README.md file.
Create a new file in this repository called `setdefaults.m`. This file is a matlab/octave
script that will set default plotting parameters. In this file, add the following lines:

    ```matlab
    set(0, 'defaultAxesFontSize', 16)
    set(0,'defaultTextFontSize',14)
    set(0,'defaultLineLineWidth',3)
    ```

    Commit the changes to your repository. 

2. Clone your 'homework_1' repository to your own computer. Create a function,
`projectile.m` that will calculate the location of an object with an initial velocity. The
function inputs are v_mag (initial speed), theta (initial angle). The output is the height
of the object 2.37 m from its starting position. Assume g=9.81 m/s^2 and its initial
height is 1.72 m. 

    ```matlab
    >> h=projectile(v_mag,theta)

      h= 1
    ```

    In addition to the output of `h`-height at 2.37 m-plot the path of the object from its
    initial position to its position at 2.37 m away from the start. *Note: use your
    `setdefaults.m` to set the plot defaults before outputting the result.*
