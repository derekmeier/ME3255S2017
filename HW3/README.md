# Homework #3
## due 2/15/17 by 11:59pm


1. Create a new github repository called 'roots_and_optimization'. 

    a. Add rcc02007 and pez16103 as collaborators.

    b. Clone the repository to your computer.

    c. Copy your `projectile.m` function into the 'roots_and_optimization' folder.
    *Disable the plotting routine for the solvers*

    d. Use the four solvers `falsepos.m`, `bisect.m`, `newtraph.m` and `mod_secant.m`
    to solve for the angle needed to reach h=1.72 m, with an initial speed of 15 m/s. 

    e. The `newtraph.m` function needs a derivative, calculate the derivative of your
    function with respect to theta, `dprojectile_dtheta.m`. This function should
    output d(h)/d(theta). 


    f. In your `README.md` file, document the following under the heading `#
    Homework #3`:

        i. Compare the number of iterations that each function needed to reach an
        accuracy of 0.00001%. Include a table in your README.md with:

        ```
        | solver | initial guess(es) | ea | number of iterations|
        | --- | --- | --- | --- |
        |falsepos   |  |  |  |
        |bisect     |  |  |  |
        |newtraph   |  |  |  |
        |mod_secant |  |  |  |
        ```

        ii. Compare the convergence of the 4 methods. Plot the approximate error vs the
        number of iterations that the solver has calculated. Save the plot as
        `convergence.png` and display the plot in your `README.md` with:

        `![Plot of convergence for four numerical solvers.](convergence.png)`

        iii. In the `README.md` provide a description of the files used to create the
        table and the convergence plot. 

2. The Newton-Raphson method and the modified secant method do not always converge to a
solution. One simple example is the function f(x) = x*exp(-x^2). The root is at 0, but
using the numerical solvers, `newtraph.m` and `mod_secant.m`, there are certain initial
guesses that do not converge. 

    a. Calculate the first 5 iterations for the Newton-Raphson method with an initial
    guess of x_i=2 for f(x)=x*exp(-x^2).

    b. Add the results to a table in the `README.md` with:

    ```
    ### divergence of Newton-Raphson method

    | iteration | x_i | approx error |
    | --- | --- | --- |
    | 0 | 2 | n/a |
    | 1 |   |     |
    | 2 |   |     |
    | 3 |   |     |
    | 4 |   |     |
    | 5 |   |     |
    ```

    c. Repeat steps a-b for an initial guess of 0.2. (But change the heading from
    'divergence' to 'convergence')

3. Commit your changes to your repository. Sync your local repository with github. Then
copy and paste the "clone URL" into the following Google Form [Homework 3](https://goo.gl/forms/UJBGwp0fQcSxImkq2)
