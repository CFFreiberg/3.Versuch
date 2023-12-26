<!--
author:   Claudia Funke

email:    claudia.funke@physik.tu-freiberg.de

version:  0.0.1

language: de

narrator: Deutsch Female

comment:  Struktur der Materie Übung 7

@style
.lia-toc__bottom {
    display: none;
}
@end


import: https://github.com/liascript/CodeRunner

import: https://raw.githubusercontent.com/LiaTemplates/Pyodide/master/README.md


-->




# Abbildung mit Slider


``` python
# Quelle: https://matplotlib.org/stable/gallery/widgets/slider_snap_demo.html
import sys
import numpy as np
import matplotlib.pyplot as plt
from matplotlib.widgets import Button, Slider
# The parametrized function to be plotted
def f(variable, m):
    return np.sin(np.pi*variable*m)**2//np.sin(np.pi*variable)**2


def main():
    x_min = -1.5
    x_max = 1.5
    x_num = 1000
    y_min = 0
    y_max = 60
    x_label = r"$\\frac{\\Delta k \\cdot a }{2\\pi}$"
    y_label = "$\\|F|^2$"
    
    # Define slider parameters
    init_m = 4
    m_min = 1
    m_max = 30
    m_step = 1
    slider_label = "Anzahl der Atome"

    x = np.linspace(x_min, x_max, x_num)
    # Create the figure and the line that we will manipulate
    fig, ax = plt.subplots()
    line, = ax.plot(x, f(x, init_m), lw=3)
    ax.set_xlabel(x_label)
    ax.set_ylabel(y_label)
    ax.set_ylim(y_min, y_max)
    # adjust the main plot to make room for the sliders
    fig.subplots_adjust(left=0.25, bottom=0.25)
    # Make a horizontal slider to control the frequency.
    axfreq = fig.add_axes([0.25, 0.1, 0.65, 0.03])
    m_slider = Slider(
        ax=axfreq,
        label=slider_label,
        valmin=m_min,
        valmax=m_max,
        valstep=m_step,
        valinit=init_m,
    )
    def update(val):
        line.set_ydata(f(x, m_slider.val))
        fig.canvas.draw_idle()
    def reset(event):
        m_slider.reset()
    # register the update function with each slider
    m_slider.on_changed(update)

    resetax = fig.add_axes([0.8, 0.025, 0.1, 0.04])
    button = Button(resetax, 'Reset', hovercolor='0.975')
    button.on_clicked(reset)   

    plt.show()
main()
```
@Pyodide.eval(`["main.py"]`, `python3 -m compileall .`, `python3 main.py`)


``` python
import matplotlib.pyplot as plt
import numpy as np

def main():
    plt.style.use('_mpl-gallery')
    
    x_label = "$\\Delta k \\cdot a_0 $"
    y_label = "$f(\\Delta k)$"
    
    # make data
    x = np.linspace(0, 10, 100)
    y = 16/(4+x**2 )**2

    # plot
    fig, ax = plt.subplots()

    ax.plot(x, y, linewidth=2.0)
    ax.set(xlim=(0, 8), xticks=np.arange(1,8,1),
        ylim=(0, 1), yticks=np.arange(0.1, 1,0.1))
        
    ax.set_xlabel(x_label)
    ax.set_ylabel(y_label)
    fig.subplots_adjust(left=0.25, bottom=0.25)


    plt.show()

main()
```
@Pyodide.eval(`["main.py"]`, `python3 -m compileall .`, `python3 main.py`)
