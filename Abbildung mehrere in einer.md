<!--
author:   Claudia Funke

email:    claudia.funke@physik.tu-freiberg.de

version:  0.0.1

language: de

narrator: Deutsch Female

comment:  Abbildung

@style
.lia-toc__bottom {
    display: none;
}
@end


import: https://github.com/liascript/CodeRunner

import: https://raw.githubusercontent.com/LiaTemplates/Pyodide/master/README.md


-->

# Abbildung mehrere in einer

``` python
# Quelle: https://matplotlib.org/stable/gallery/widgets/slider_snap_demo.html

import sys
import numpy as np
import matplotlib.pyplot as plt


# The parametrized function to be plotted
def f1(variable):
    return 1/variable**12
def f2(variable):
    return -1/variable**6
def f3(variable):
    return (1/variable**12)-(1/variable**6)


def main():
    x_min = 0.8
    x_max = 1.8
    x_num = 100
    y_min = -1
    y_max = 1
    x_label = r"$\\dfrac{R }{\\sigma}$"
    y_label = r"$\\dfrac{U }{\\varepsilon}$"
    x = np.linspace(x_min, x_max, x_num)
    fig, ax = plt.subplots()
    line, = ax.plot(x, f1(x),'r--')
    line, = ax.plot(x, f2(x),'b--')
    line, = ax.plot(x, f3(x),'g')
    plt.legend((r"$+\\left (\\dfrac{\\sigma}{R}\\right)^{12}$", r"$-\\left (\\dfrac{\\sigma}{R}\\right)^{6}$", r"$+\\left (\\dfrac{\\sigma}{R}\\right)^{12}-\\left (\\dfrac{\\sigma}{R}\\right)^{6}$" ),loc='upper center', shadow=True)
    plt.grid(True)
    ax.set_xlabel(x_label)
    ax.set_ylabel(y_label)
    ax.set_ylim(y_min, y_max)
    
    plt.show()
main()
```
@Pyodide.eval(`["main.py"]`, `python3 -m compileall .`, `python3 main.py`)